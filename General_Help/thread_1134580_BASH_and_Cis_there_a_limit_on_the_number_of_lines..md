---
title: "BASH and C:is there a limit on the number of lines..."
date: 2009-04-23
forum: General Help
---

### Post by 3l3vans on 2009-04-23
is there a limit on the number of lines BASH can display at once? if there is, is there a way to change the limit? 
     i have been teaching myself C from a book and i have been working on a program that basically counts from one to a thousand on seperate lines. no matter what i do the first line is always cut off.if i change the variables then i get the same result with the first line (no matter where my starting point is) not being displayed.
     i am almost certain that this is an issue with bash and not my program (i've been ove it a hundred times and like i said when i change the variabe i still lose the first line somehow.) for what it is worth here is the code:


#include <stdio.h>

int main()
{
        int packet;

        printf("Processing 1000 packets:\n");
        for(packet=0;packet<1000;packet=packet+1)
        {
                printf("Doing amazing things with packet#%d\n",packet+1);
        }
        return(0);
}


now no matter how i change the values in the "for" line,after compiling and running, i still come up with the first line ("Doing amazing things with packet#1") not being displayed. it starts at #2. its not  huge deal, but i would like to understand what is happening.

---

