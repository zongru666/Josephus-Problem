# 约瑟夫问题
/*据说著名犹太历史学家 Josephus 有过以下故事：在罗马人占领乔塔帕特后，
39 个犹太人与 Josephus 及他的朋友躲到一个洞中，39 个犹太人决定宁愿死也不要被敌
人抓到，于是决定了一种自杀方式，41 个人排成一个圆圈，由第 1 个人开始报数，报数
到 3 的人就自杀，然后再由下一个人重新报 1，报数到 3 的人再自杀，这样依次下去，
直到剩下最后一个人时，那个人可以自由选择自己的命运。这就是著名的约瑟夫问题。现
在请用单向环形链表得出最终存活的人的编号。*/

## //输入描述：一行两个整数 n 和 m， n 表示环形链表的长度， m 表示每次报数到 m 就自杀。
## //输出描述：输出最后存活下来的人编号(编号从1开始到n)

#include<iostream>  
using namespace std; 
///////////////////////数学解法//////////////////////////////
// int main() {
    // int n,m;  
    // cin>>n>>m;  
    // int r=1;  
    // for(int i=2;i<=n;i++){  
        // r=(r+m)%i;  //上一轮编号
        // if(r==0)r=i;
    // }  
    // cout<<r;
    // // system("pause");
    // return 0;
// }
 
 
///////////////////////环形链表解法//////////////////////////////
//create struct node 
struct node{
    int data;
    struct node next;
};
 
int main(){
    int n,m;
    cin>>n>>m;
    node head=new node;
    node *p=head;
    head->data=1;
    // head->next=nullptr;
    for(int i=2;i<n+1;i++){
        p->next=new node;
        p=p->next;
        p->data=i;//编号
        if(i==n){
            p->next=head;
        }
    }
    p=head;
    for(int i=1;i<n;i++){
        for(int j=1;j<m-1;j++){
            p=p->next;
        }
        p->next=p->next->next;
        p=p->next;
    }
    cout<<p->data;
    system("pause");
    return 0;
}
