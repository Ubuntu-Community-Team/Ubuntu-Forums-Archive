---
title: "compiation of sqrt funtion in C"
date: 2012-06-10
forum: Education &amp; Science
---

### Post by dharmes on 2012-06-10
i have written a program,
were i have to find a square root of a function.
but i get the following error while compilation.

dharmesh@dharmesh-ThinkPad-SL400:~/bg/ch5$ gcc -Wall  p10.c -o p10.o
/tmp/cckBRHAS.o: In function `main':
p10.c:(.text+0xf0): undefined reference to `sqrt'
p10.c:(.text+0x134): undefined reference to `sqrt'
collect2: ld returned 1 exit status
dharmesh@dharmesh-ThinkPad-SL400:~/bg/ch5$ 

i have used the header file math.h, and can't find any error in my simple program,
kindly give a sol to my problem!

---

### Post by sudodus on 2012-06-10
Probably you need to add -lm for the linker. Say that your file sqrt.c contains the following code
```
/* Square root of a number using Built-In Function */

#include <stdio.h>
#include <math.h>

void main()
{
 double n,r;
 double sqrt(double n);
 printf("Enter the no.: ");
 scanf("%lf",&n);
 r=sqrt(n);
 printf("The root of %6.4lf is %6.4lf",n,r);
}
```

Then you can compile and link it with the following command line
```
cc -o sqrt sqrt.c -lm
```

---

