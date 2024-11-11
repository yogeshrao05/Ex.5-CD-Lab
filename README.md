# Ex-5-RECOGNITION-OF-THE-GRAMMAR-anb-where-n-10-USING-YACC
RECOGNITION OF THE GRAMMAR(anb where n>=10) USING YACC
# Date: 17.10.2024
# Aim:
To write a YACC program to recognize the grammar anb where n>=10.
# ALGORITHM
1.	Start the program.
2.	Write a program in the vi editor and save it with .l extension.
3.	In the lex program, write the translation rules for the variables a and b.
4.	Write a program in the vi editor and save it with .y extension.
5.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
6.	Compile the yacc program with yacc compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
7.	Compile these with the C compiler as gcc lex.yy.c y.tab.c
8.	Enter a string as input and it is identified as valid or invalid.
# PROGRAM:
### anb.l
```
%{
#include "y.tab.h"
#include <stdio.h>
%}

/* Rule Section */
%%

[aA] { return A; }
[bB] { return B; }
\n { return NL; }
. { /* Ignore any other characters */ }

%%


int yywrap() {
    return 1;
}
```
### anb.y
```
%{
#include <stdio.h>
#include <stdlib.h>

void yyerror(char *s);
int yylex(void);
%}

%token A B NL

%% 

stmt: S NL { printf("Valid string\n"); exit(0); }
;

S: A S B | /* Allow for empty production */
  
;

%% 

void yyerror(char *s) {
    fprintf(stderr, "Invalid string\n");
}

int main() {
    printf("Enter the string:");
    yyparse();
    return 0;
}

```
# OUTPUT
### VALID STRING
![Screenshot from 2024-10-22 11-43-35](https://github.com/user-attachments/assets/1b1189d4-7b5f-4d1a-bd2d-02ce99a6c176)
### INVALID STRING
![Screenshot from 2024-10-22 11-42-31](https://github.com/user-attachments/assets/5cf59994-92ff-4c4f-9ab9-2272089f9392)

# RESULT
The YACC program to recognize the grammar anb where n>=10 is executed successfully and the output is verified.
