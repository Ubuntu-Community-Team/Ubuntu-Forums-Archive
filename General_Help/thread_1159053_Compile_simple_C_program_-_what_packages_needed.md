---
title: "Compile simple C program - what packages needed"
date: 2009-05-14
forum: General Help
---

### Post by superjacent on 2009-05-14
I'm attempting to compile the following C program:

```
#include <stdio.h>
int main()
{
  printf("Hello World\n");
  exit(0);
}
```

At the command line:

```
steven@steven-linux-desktop:~/Documents/ProgrammingLinux$ gcc -o hello hello.c
hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:4: warning: incompatible implicit declaration of built-in function ‘printf’
hello.c:5: warning: incompatible implicit declaration of built-in function ‘exit’
steven@steven-linux-desktop:~/Documents/ProgrammingLinux$    
```

What other packages do I need to install or fiddle with to make this compile properly?

Any advice appreciated.

---

### Post by skirkpatrick on 2009-05-14
The only thing you should have to install is **build-essential**.

---

### Post by saidinesh5 on 2009-05-14
the package is called build-essentials

if you have your ubuntu installation dvd , then in that you can readily find the build essentials package in 
/pool/main/b/

---

### Post by superjacent on 2009-05-14
Thank you all.   Just for my own reference (maybe others as well) I did the following.   

```
apt-get install build-essential
```

*This helps me when looking over my own threads months later.*

@SkirkPatrick - great signature line.

---

