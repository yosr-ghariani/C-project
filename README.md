#include <stdio.h>
#include <stdlib.h>
struct produit{ 
int id ;
char name[20];
 char desc[200];
  int quant ;
  float price ;
};

void recherche(int id)
{

    FILE *infile;
    struct produit p;


    infile = fopen ("products.txt", "r");
    if (infile == NULL)
    {
        fprintf(stderr, "\nError opening file\n");
        exit (1);
    }


    while(fread(&p, sizeof(struct produit), 1, infile)){
        if(p.id==id){
        printf(" id:%d \n name: %s \n description: %s \n quantité:%d \n price:%f \n",p.id,p.name,p.desc,p.quant,p.price);}
        }
    printf("there is no product with this id!");



    fclose (infile);

}


void modifier(int id){
    int x;
    FILE *infile;
    struct produit p;


    infile = fopen ("products.txt", "r");
    if (infile == NULL)
    {
        fprintf(stderr, "\nError opening file\n");
        exit (1);
    }


    while(fread(&p, sizeof(struct produit), 1, infile)){
        if(p.id==id){
        printf("what are you going to change?\n press 1 for name \n press 2 for description \n press 3 for quantity \n press 4 for price\n ");
        scanf(" %d",&x);
        switch(x){
        case 1:
            printf("give me a new name");
            scanf(" %s",&p.name);
            break;
        case 2:
            printf("write your new description ");
            scanf(" %s",&p.desc);
            break;
        case 3:
            printf("write your new quantity");
            scanf(" %d",&p.quant);
            break;
        case 4:
            printf("write your new price");
            scanf(" %f",&p.price);
            break;
            }}}
    printf("there is no product with this id!");



    fclose (infile);

}
