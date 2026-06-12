---
title: "the GDB does not show the proper output when breakpoints are put"
date: 2009-01-05
forum: General Help
---

### Post by rahulpawar on 2009-01-05
hi
i am a two day old ubuntu fan. i got gdb installed on the system and did the following:

1. write a program which has the following code
int main()
{
    struct timeval tv;

    if(gettimeofday(&tv,NULL)==0)
        printf("the year from 1970 is:\n%d",(((tv.tv_sec)/3600)/24)/365);
    return 0;
}

i know this is a crude code. but this gives the year from the 1970. that is it should give 39 as the output.

2. g++ -g function.c
3. gdb ./a.out
4.b main
5.run
6.n
7. continue step 6 till end of the program

*************************************************
expected output:
the year from 1970 is:
39

actual output:
the year from 1970 is:

************************************************

can someone here point out why the gdb does not give the correct output here?

---

