---
title: "Still can't get 855resolution to install - won't compile!"
date: 2006-03-10
forum: Desktop Environments
---

### Post by sheilnaik on 2006-03-10
I apologize for such a dumb question, but I've been trying to figure this out for a long time and still can't get it to work.  Linux is also very new to me, so I'm having trouble with even basic commands.

I have a Dell 700m with Ubuntu installed, and I'm trying to get the 855resolution driver to install so I can get a 1200x800 resolution working.  I downloaded and extracted the tar.gz file, and according to the instructions, the next step is to navigate to the directory and use the "make" command.  However, whenever I try to use "make", I get the following error:

```

sheil@ubuntu:~/855resolution$ make
cc -Wall -I`pwd` -DVERSION='"0.4"' -DPLUGINS='plugin1,plugin2,plugin3' -DREF_PLUGINS='&plugin1,&plugin2,&plugin3'    -c -o 855resolution.o 855resolution.c
855resolution.c:14:19: error: stdio.h: No such file or directory
855resolution.c:15:20: error: stdlib.h: No such file or directory
855resolution.c:16:20: error: string.h: No such file or directory
855resolution.c:17:20: error: unistd.h: No such file or directory
855resolution.c:18:20: error: sys/io.h: No such file or directory
855resolution.c: In function ‘find_modes’:
855resolution.c:31: error: ‘NULL’ undeclared (first use in this function)
855resolution.c:31: error: (Each undeclared identifier is reported only once
855resolution.c:31: error: for each function it appears in.)
855resolution.c:42: warning: control reaches end of non-void function
855resolution.c: In function ‘find_resolution’:
855resolution.c:53: error: ‘NULL’ undeclared (first use in this function)
855resolution.c:54: warning: control reaches end of non-void function
855resolution.c: In function ‘list_modes’:
855resolution.c:63: warning: implicit declaration of function ‘printf’
855resolution.c:63: warning: incompatible implicit declaration of built-in function ‘printf’
855resolution.c: In function ‘parse_args’:
855resolution.c:79: error: ‘NULL’ undeclared (first use in this function)
855resolution.c:81: warning: implicit declaration of function ‘strlen’
855resolution.c:81: warning: incompatible implicit declaration of built-in function ‘strlen’
855resolution.c:99: warning: implicit declaration of function ‘atoi’
855resolution.c:101: warning: implicit declaration of function ‘fprintf’
855resolution.c:101: warning: incompatible implicit declaration of built-in function ‘fprintf’
855resolution.c:101: error: ‘stderr’ undeclared (first use in this function)
855resolution.c:122: warning: implicit declaration of function ‘strtol’
855resolution.c: In function ‘usage’:
855resolution.c:130: warning: incompatible implicit declaration of built-in function ‘printf’
855resolution.c: In function ‘main’:
855resolution.c:140: error: ‘NULL’ undeclared (first use in this function)
855resolution.c:147: warning: incompatible implicit declaration of built-in function ‘printf’
855resolution.c:160: warning: implicit declaration of function ‘iopl’
855resolution.c:161: warning: implicit declaration of function ‘perror’
855resolution.c:172: warning: incompatible implicit declaration of built-in function ‘fprintf’
855resolution.c:172: error: ‘stderr’ undeclared (first use in this function)
855resolution.c:181: warning: incompatible implicit declaration of built-in function ‘fprintf’
855resolution.c:190: warning: incompatible implicit declaration of built-in function ‘fprintf’
855resolution.c:195: warning: implicit declaration of function ‘putchar’
855resolution.c:206: warning: incompatible implicit declaration of built-in function ‘fprintf’
make: *** [855resolution.o] Error 1
sheil@ubuntu:~/855resolution$

```

It seems to me that it can't find the compiler to "make" the driver.  However, I have GCC (and GCC+) both installed from the Synaptic Package Manager, as well as the "make" package.

What am I doing wrong or what I am forgetting?

---

### Post by stuporglue on 2006-03-10
You actually need more than just gcc to compile most programs. Install the package "build-essential"...it'll pull the other stuff you need.

---

### Post by issueperson on 2006-03-11
before you run the "make" command you should navigate to the directory and type:

```
./config
```

let it do its thing, and then use the make and make install commands.

but like the previous post said, you might need to install some other stuff first too.  try:

```
sudo apt-get install build-essential
```

issueperson

---

### Post by sheilnaik on 2006-03-11
Ah, ok.  I was trying ./configure.  That's probably what messed me up.  Thanks a lot, it helped!

---

### Post by issueperson on 2006-03-11
[QUOTE=sheilnaik]Ah, ok.  I was trying ./configure.  That's probably what messed me up.  Thanks a lot, it helped![/QUOTE]

no problem.  is it working?

---

### Post by sheilnaik on 2006-03-11
I'm not sure if it actually works.  I just installed the 855resolution file from the Synaptic Package Manager and it worked fine.  However, I'll remember the ./config command for later when I have to install files in the future.  Thanks for all your help.

---

