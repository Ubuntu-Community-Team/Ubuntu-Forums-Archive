---
title: "end of stream vs. end of file"
date: 2009-05-05
forum: General Help
---

### Post by vegeta7794 on 2009-05-05
Hi, i have a part of a c-program:

 typedef struct { int* Value; int Row; int Col;} Matrix;
Matrix *matrix;

 int i,j;
    int value;
    f = fopen(fileName, "w");
    if(!f)
        return;
    fprintf(f, "%d\n", matrix->Row);
    fprintf(f, "%d\n", matrix->Col);
    for(i = 0; i < matrix->Row; i++)
    {   for(j = 0; j < matrix->Col; j++)
        {   GetElt(matrix, i+1, j+1, &value);  //it'll get value at position [i+1,j+1] of matrix
            
           [B] if(j+1 == matrix->Col)
                fprintf(f, "%d\n", value);
            else
                fprintf(f, "%d\t", value);[/B]

        }
    }
    fclose(f);
problem here is in bold part, with these line i think it'll write to file all elements of the matrix by format:
ex. matrix 3x3:

3
3
1 [tab] 2 [tab] 3 [end line]
4 [tab] 5 [tab] 6 [end line]
7 [tab] 8 [tab] 9 [end line]
[new line here]                              // i need this new line
but when i implemented with ubuntu 8.10, it didn't result like that, the new line at the end wasn't printed.
I really want to know how ubuntu treated with [end of stream] and [end of file]? sorry, i'm weak at english. Thanks.

---

