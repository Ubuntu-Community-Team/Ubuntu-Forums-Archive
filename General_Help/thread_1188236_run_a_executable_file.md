---
title: "run a executable file"
date: 2009-06-15
forum: General Help
---

### Post by subjugater on 2009-06-15
My friend forwarded my a executable file which was made by compiling a fortran code. 

I tried to execute it by typing:

> kuan@kuan-desktop:~/Desktop/jiang/ver3$ ./testdriver


But I ended up with 

> bash: ./testdriver: cannot execute binary file

Anybody know what I should do? Thanks.

ps. I have checked the file permission. It is executable with 3 x's in the mode display line.

---

### Post by s.fox on 2009-06-15
Hi,

If its an .exe file you will need wine to run it.  [Here]("https://help.ubuntu.com/community/Wine") is some more information on it.  Wine is also listed in synaptic package manager. :)

-Ash R

---

### Post by subjugater on 2009-06-15
> **Ash R said:**
> Hi,

If its an .exe file you will need wine to run it.  [Here]("https://help.ubuntu.com/community/Wine") is some more information on it.  Wine is also listed in synaptic package manager. :)

-Ash R

Thanks, buddy. Unfortunately, it is not a .exe file, since it doesn't have a extensional name and it was generated in a linux system.

---

### Post by Amilo1718 on 2009-06-15
chmod doesn't do the trick ?

---

### Post by DGortze380 on 2009-06-15
> **subjugater said:**
> My friend forwarded my a executable file which was made by compiling a fortran code. 

I tried to execute it by typing:



But I ended up with 



Anybody know what I should do? Thanks.

ps. I have checked the file permission. It is executable with 3 x's in the mode display line.

Get the source from your friend and compile it on your machine.
Are you running x86 or x86_64?
What about your friend?

---

### Post by subjugater on 2009-06-15
> **DGortze380 said:**
> Get the source from your friend and compile it on your machine.
Are you running x86 or x86_64?
What about your friend?

Thanks, buddy. The thing is my friend's codes can only be compiled by ifort which I really don't have ('coz I failed to install it on my computer). Other compilers such as gfortran or g95 can not compile it successfully.

Anyhow, thanks.

---

