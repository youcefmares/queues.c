# queues.c
#include <stdio.h>
#include <stdlib.h>

typedef struct node {
     int custumernumber;
      struct node *next;
       } node;


typedef struct queue {
     node *front;
      node *rear;
       } queue;


void initqueue(queue*q){
    q->front=NULL;
    q->rear=NULL;

}
int isempty(queue *q){
    return q -> front == NULL;
}

void enqueue(queue*q,int number){
    node *newcustumer = (node*) malloc(sizeof(node));

    if (newcustumer == NULL){
        return;
    }

    newcustumer ->custumernumber = number;
    newcustumer -> next =NULL;

    if(isempty(q)){
        q->front =newcustumer ;
        q->rear = newcustumer;

    }
    else{
        q->rear->next = newcustumer;
        q->rear = newcustumer;

    }
}
int dequeue(queue*q){
    if(isempty(q))return-1;

    node*temp = q-> front;
    int number = temp ->custumernumber;
    q->front = q->front->next;

    if (q->front ==NULL){
        q->rear = NULL;
    }
    free(temp);
    return number;
}

int peek(queue *q){
    if(isempty){
        return -1;
    }
    return q->front->custumernumber;

}


int main(){
    queue q;
    enqueue(&q,10);
    printf("custumer in queue = %d\n ",peek(&q));
    enqueue(&q,10);
    printf("custumer in queue = %d ",dequeue(&q));

return 0;
}