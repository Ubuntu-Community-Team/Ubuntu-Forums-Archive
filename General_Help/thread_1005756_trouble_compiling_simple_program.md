---
title: "trouble compiling simple program"
date: 2008-12-08
forum: General Help
---

### Post by zero777zero on 2008-12-08
i've read at least 5 compiling guides 5 times over and none of them have helped me compile either program i've tried it on. i tried the guide on the ubuntu forums, but it doesnt seem relevant to what i'm trying to compile.

i'm trying to compile a simple program called ECM

here is the name of the source code file: ecm.c

here is what is in the README.txt file that comes along with the source code: "Compile ecm.c and unecm.c if necessary, or use the included Win32 EXE files." no further instructions.

the cd is set to the proper location

here is what i tried to do:

MYUSERNAME@yakuzaBOX:~$ cd /home/MYUSERNAME/Desktop/ecm100

MYUSERNAME@yakuzaBOX:~/Desktop/ecm100$ ./configure

bash: ./configure: No such file or directory

MYUSERNAME@yakuzaBOX:~/Desktop/ecm100$ ./ecm.c

bash: ./ecm.c: Permission denied

MYUSERNAME@yakuzaBOX:~/Desktop/ecm100$ make

make: *** No targets specified and no makefile found.  Stop.


what did i do wrong? i know of someone else who compiled this already on linux.

---

### Post by lovelyvik293 on 2008-12-08
When you have to compile a c file then use the gcc compiler like 
```
gcc ecm.c
```
Which produce the a.out file and then you can run this a.out file like
```
./a.out
```

---

### Post by cmay on 2008-12-08
make sure you have the build-essential package installed.

---

### Post by zero777zero on 2008-12-08
thanks! worked fine :p

---

