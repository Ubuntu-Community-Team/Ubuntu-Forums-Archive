---
title: "Makefile"
date: 2012-06-29
forum: Education &amp; Science
---

### Post by pjgarde on 2012-06-29
we are a groups of student of an Argentina university and need help to do a Makefile, we have to do one and no have any idea of how.... If someone know and want to tell us. We will apreciate your answer.

I want to compile this...

main.c

#include <stdio.h>
#include <funcion1.h>

int main(void)
{
    escribeHolaMundo();    
    return 0;
} 

funcion1.c

#include <stdio.h>
#include "funcion1.h"

void escribeHolaMundo(void)
{
   printf("Hola Mundo\n");
} 

funcion1.h

void escribeHolaMundo(void);

---

### Post by gardnan on 2012-06-29
It depends on how complex you want to have your build process. There tend to be a large number of conventions that go into writing makefiles, but a very basic layout of one follows:

```

program : main.o funcion.o
         gcc -Wall -g -o program main.o funcion.o

main.o : main.c
         gcc -Wall -g -c -o main.o main.c

funcion.o : funcion.c
         gcc -Wall -g -c -o funcion.o function.c 

```

This code does not have proper spacing, so you can't directly copy/paste it.

Also, generally in a makefile, the actual system commands, targets, and source files are encapsulated in variables. Here is a link to the GNU Make manual. Also, including "funcion.h" in brackets may cause it to fail. Try switching that to be in quotes.

[http://www.gnu.org/software/make/manual/]("http://www.gnu.org/software/make/manual/")

---

### Post by raja.genupula on 2012-06-29
[http://markuskimius.wikidot.com/programming:tut:autotools:2](http://markuskimius.wikidot.com/programming:tut:autotools:2)

---

### Post by nothingspecial on 2012-06-29
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

Closed.

---

