---
title: "simple question of using gcc compile"
date: 2009-03-11
forum: General Help
---

### Post by oasi on 2009-03-11
Hello, 

I am new here, and it is not a long time since i installed ubuntu8.10 in my pc. i try to compile a simple program C with gcc, but there are pbs ...

--- i tryed:
$ gcc secu.c
--- then, there is a file a.out generated, then:
$ make a.out
make: Rien à faire pour « a.out ».
--- so, i think the a.out may be an execute file:
$ a.out
bash: a.out : commande introuvable
--- really don't understand why ...

--- so i tryed another way:
$ cc -c secu.c
$ cc -o secu secu.c
$ make secu
  make: « secu » est à jour
$ secu
  bash: secu : commande introuvable
--- it still doesn't work

Do you have any idea ? 

i also checked the version of gcc
$ gcc --version
  gcc (Ubuntu 4.3.2-1ubuntu12) 4.3.2

Hoping for some help. Thanks a lot!

---

### Post by oasi on 2009-03-11
up up 
waiting for some help

---

### Post by heindsight on 2009-03-11
If your program is in a file called foo.c and you do:
```
gcc foo.c
```
then gcc will compile foo.c and generate an executable called a.out

You can also do:
```
gcc -o foo foo.c
```
in which case gcc will compile foo.c and generate an executable called foo.

Unless the directory containing your executable is listed in the PATH environment variable, which you can examine using the command:
```
echo $PATH
```
you have to supply the path to the executable to run it.

In other words, if foo is an executable in your current directory (not listed in $PATH) then do:
```
./foo
```
to run foo

---

### Post by oasi on 2009-03-11
Thank you heindsight!

it works now :)

---

