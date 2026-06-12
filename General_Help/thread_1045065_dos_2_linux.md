---
title: "dos 2 linux"
date: 2009-01-20
forum: General Help
---

### Post by masali on 2009-01-20
Hello, 
if i have a c code  written in dos enviroment, can i convert it to linux. 
those are the libraries used by my code (if this information is relevant)
#include <dos.h>

#include <conio.h>

#include <stdio.h>

#include <string.h>
thanks

---

### Post by iaculallad on 2009-01-20
Compiling C codes in DOS is similar with Linux.

To compile the source code (say, sample.c):

```
cc -c sample.c
```

To create the executable file:

```
cc -o sample.c
```

and to execute it:

```
./sample
```

You don't have to change any coding syntax.

HTH.

EDIT: Do not forget to install the build-essential package.

```
sudo apt-get install build-essential
```

---

### Post by masali on 2009-01-20
Thanks for the reply. When i compile the code as it is i get the following errors:
```
 gcc -o serial serialz14a.c
 error: dos.h: No such file or directory
 error: conio.h: No such file or directory
 error: expected declaration specifiers or &#8216;...&#8217; before &#8216;*&#8217; token
 error: &#8216;interrupt&#8217; declared as function returning a function
 error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;com_int&#8217;
 In function &#8216;setvects&#8217;:
 error: &#8216;oldvects&#8217; undeclared (first use in this function)
 error: (Each undeclared identifier is reported only once
 error: for each function it appears in.)
 error: &#8216;com_int&#8217; undeclared (first use in this function)
 In function &#8216;resvects&#8217;:
 error: &#8216;oldvects&#8217; undeclared (first use in this function)
 In function &#8216;SetPort&#8217;:
error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
&#8216;RS232_Addr&#8217; undeclared (first use in this function)
 At top level:
 error: stray &#8216;\32&#8217; in program
```

I guess I'm also asking whether there exists a c library in linux that corresponds to the dos.h and conio.h that I use in Windows?

---

### Post by pansz on 2009-01-20
#include <dos.h>
#include <conio.h>
#include <stdio.h>
#include <string.h>

when in doubt, always check the standard compliance before using a lib function. Linux has most POSIX-compliant lib-functions.

in your case, the <dos.h> and <conio.h> does not exist, you may need to replace with <unistd.h> and ncurse lib, but the underlying function interfaces are totally different and you may need to re-write a big part of your program.

for serial communications, linux uses the fd read and write, dos uses interrupt.

This might be a major rewrite of the program.

---

### Post by masali on 2009-01-25
thanks for the reply.

---

