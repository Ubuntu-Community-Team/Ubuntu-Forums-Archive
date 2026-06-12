---
title: "installing turbo c/c++"
date: 2009-06-13
forum: General Help
---

### Post by becoolpal on 2009-06-13
how can i install turbo c cpp on ubuntu
i have installed DOSBOX but nothing is working
please help me....!

---

### Post by 7raTEYdCql on 2009-06-13
Why turbo C.
Move on to better things, there is GCC which will help you in compiling your C code.

Turbo C has no match fo r GCC's capabilities, so move on.

And as far as compiling code in GCC these are the following:

gcc name.c -o name
./name

The last part (-o name) is not necessary.
If not used then instead of ./name run ./a.out

---

### Post by rCXer on 2009-06-13
What do you mean by nothing works? Are you getting an error?  Unless you *really* want a DOS program, you should do as i.mehrzad suggested and use gcc.

---

### Post by becoolpal on 2009-07-01
i mean i mounted the drive as c:
& from there i tried to run turbo c.exe but its not working
anyways please tell me how to work with gcc .As i m a beginner to this O.S so please guide me step by step .

---

### Post by colau on 2009-07-01
> **becoolpal said:**
> i mean i mounted the drive as c:
& from there i tried to run turbo c.exe but its not working
anyways please tell me how to work with gcc .As i m a beginner to this O.S so please guide me step by step .
Install g++
```

sudo apt-get install g++

```
Go to that directory with .cpp or .c files.
```

g++ filename.cpp -o filename
./filename

```

---

### Post by WRDN on 2009-07-01
If you don't want to compile from the terminal, or write a Makefile, then, I would suggest using an IDE (Integrated Development Environment).
I would recommend NetBeans and Code::Blocks for C/C++. These can be installed with the command:

```
sudo apt-get install netbeans codeblocks
```

---

### Post by 3Miro on 2009-07-01
Try Geany (use Add/Remove), it will let you edit code very easily. Then you can set it up to call the makefile (google makefile for tutorial on how to write one, it isn't very hard).

---

### Post by colau on 2009-07-01
```

sudo aptitude install codelite

```

---

### Post by gavarchand on 2011-06-21
> **becoolpal said:**
> how can i install turbo c cpp on ubuntu
i have installed DOSBOX but nothing is working
please help me....!.

---

