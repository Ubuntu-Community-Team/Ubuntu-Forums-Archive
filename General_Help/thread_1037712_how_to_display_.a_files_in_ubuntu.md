---
title: "how to display .a files in ubuntu"
date: 2009-01-12
forum: General Help
---

### Post by prick.i.am on 2009-01-12
Hi all,
i've downloaded an application "lp_solve_dev.tar.gz"...
but the file with .a extension is not being displayed... 
its a library file...
wat do i do?

---

### Post by hivelocitydd on 2009-01-12
which version of ubundu you are using ?

---

### Post by prick.i.am on 2009-01-12
> **hivelocitydd said:**
> which version of ubundu you are using ?

Hardy heron 8.4

---

### Post by lian1238 on 2009-01-12
Can't you open it with a text editor?

---

### Post by prick.i.am on 2009-01-12
> **lian1238 said:**
> Can't you open it with a text editor?

nope..
doesnt open wit txt editor

---

### Post by lian1238 on 2009-01-12
If you could give us the link to the file you downloaded, maybe someone can tell you how to use it.

---

### Post by prick.i.am on 2009-01-12
> **lian1238 said:**
> If you could give us the link to the file you downloaded, maybe someone can tell you how to use it.


lp_solve_5.5.0.13_dev.tar.gz   

from:
[http://sourceforge.net/project/showfiles.php?group_id=145213&package_id=159735](http://sourceforge.net/project/showfiles.php?group_id=145213&package_id=159735)

the file name is liblpsolve55.a

---

### Post by mssever on 2009-01-12
> **prick.i.am said:**
> nope..
doesnt open wit txt editor
Every file except symlinks and perhaps some special files can be opened in a text editor. You just have to use a sufficiently-sane editor. Try opening it in vim or bless, or doing ```
hd thefile | less
```

---

### Post by prick.i.am on 2009-01-12
> **mssever said:**
> Every file except symlinks and perhaps some special files can be opened in a text editor. You just have to use a sufficiently-sane editor. Try opening it in vim or bless, or doing ```
hd thefile | less
```

yup 
tat cmd worked....
Thx bro...
But i cudnt understand a  single thing tat file said:confused:

---

### Post by lian1238 on 2009-01-12
It's apparently a binary file. Reading it with nano shows that the first line is !<arch> so I'm guessing it's an Arch Linux executable. (?)

Extracting it with ar gives you a bunch of .o (object) files.

---

### Post by mssever on 2009-01-12
If you type ```
file thefile
```the system will try to guess the file's type. That might provide some useful information.

---

### Post by dragos240 on 2009-01-12
I think thats a c++ file or something.

---

### Post by prick.i.am on 2009-01-12
> **lian1238 said:**
> It's apparently a binary file. Reading it with nano shows that the first line is !<arch> so I'm guessing it's an Arch Linux executable. (?)

Extracting it with ar gives you a bunch of .o (object) files.

it it an arch executable...
so gotta extract with ar????
thx.....

---

### Post by prick.i.am on 2009-01-12
> **mssever said:**
> If you type ```
file thefile
```the system will try to guess the file's type. That might provide some useful information.

yup its a current ar archive

---

### Post by prick.i.am on 2009-01-12
> **lian1238 said:**
> It's apparently a binary file. Reading it with nano shows that the first line is !<arch> so I'm guessing it's an Arch Linux executable. (?)

Extracting it with ar gives you a bunch of .o (object) files.

how do i extract with ar????
i mean is der a explicit cmd????
rather than jus extractin wit archive....

---

### Post by heindsight on 2009-01-12
Opening that file with a text editor won't do you much good. I'm not sure exactly what it is you want to do, but the tarball you downloaded contains header files and libraries needed to compile and link C programs using liblpsolve. You could put these files under /usr/local/lib (for the .so and .a files) and /usr/local/include (for the .h files) and then after running ldconfig you should be able to compile programs using liblpsolve - you may have to do more, it's been years since i've needed to manually install a library like this.

You'd be much better off just installing liblpsolve55-dev from the ubuntu repositories by doing ```
sudo aptitude install liblpsolve55-dev
```.
After that you won't need to do anything special to compile programs using liblpsolve.

---

### Post by lian1238 on 2009-01-12
> **prick.i.am said:**
> how do i extract with ar????
i mean is der a explicit cmd????
rather than jus extractin wit archive....

Try reading the manual.
```
man ar
```

If you're not sure how to use a program, run man on it.

Reading the manual will tell you to use the flag -x to extract the archive.

---

