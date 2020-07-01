# Analisador-Lexico
%{
 #include <stdio.h>
 #include <stdlib.h>
 int Mai=0,Min=0,Keyword=0,colc=0,paren=0, op=0, pnt=0;
%}
/* Sempre que for utilizar keywords é necessário
declarar antes da regas gerais ( as regras não podem
se sobrepor )
 Ex. "if" e [a-z]
*/
%%
"if" printf("Keyword condicional");Keyword++;
"then" printf("Keyword condicional");Keyword++;
"to" printf("Keyword condicional");Keyword++;
"do" printf("Keyword condicional");Keyword++;
"else" printf("Keyword condicional");Keyword++;
"for" printf("Keyword condicional");Keyword++;
"while" printf("Keyword condicional");Keyword++;
"print" printf("Keyword condicional");Keyword++;
"printf" printf("Keyword condicional");Keyword++;
"scanf" printf("Keyword condicional");Keyword++;
"["|"]" printf("Colchete");colc++;
"("|")" printf("Parentese");paren++;
";" printf("Ponto e virgula");pnt++;
"<"|">" printf("Operador relacional");op++;
"=="|"!=" printf("Operador relacional");op++;
"<=" printf("Operador relacional");op++;
">=" printf("Operador relacional");op++;
[A-Z]+ printf("Identificador maiusculo \t");Mai++;
[a-z]+ printf("Identificador minusculo \t");Min++;
"///" printf("\n\n\n Finalizando o codigo.... \n\n\n");return 0 ;
%%
void func(){
 printf("Identificadores Maiusculos: %i \n",Mai);
 printf("Identificadores Minisculos: %i \n",Min);
 printf("Colchetes: %i \n",colc);
 printf("Parenteses: %i \n",paren);
 printf("Operadores relacionais: %i \n",op);
 printf("Ponto e virgula: %i \n",pnt);
 printf("Keywords: %i \n\n", Keyword);
 printf("Total de tokens: %i \n\n",
Keyword+Mai+Min+colc+paren+op+pnt);
}
int main(){

 yylex();
 system("cls");
 func();
}
int yywrap(){
 return 1;
}
