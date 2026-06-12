---
title: "HELP getting a file from a cvs and installing it!!!!"
date: 2005-11-27
forum: Desktop Environments
---

### Post by %hMa@?b&lt;C on 2005-11-27
I really need (and i mean need) to get and install this one program "pv2tool-for-linux" and dont know anytihgn about compiling and stuff.
it is located here
[http://cvs.sourceforge.net/viewcvs.py/pv2devkit/](http://cvs.sourceforge.net/viewcvs.py/pv2devkit/)
in desperate need of help.

---

### Post by stalefries on 2005-11-27
Try googling for "compliling programs from cvs"

---

### Post by %hMa@?b&lt;C on 2005-11-28
[QUOTE=stalefries]Try googling for "compliling programs from cvs"[/QUOTE]
couldn't find any thing helpful, link please.

---

### Post by duan on 2005-11-28
I don't know that much but i only recently got some cvs stuff installed and compiled so here goes a starter that will get you the files and see if it means anything to you:

there are several cvs tools available but the standard cvs tool is installed on your linux, guaranteed. 

all you need to do is to let cvs know what it is you want and the simplest way is to use your terminal. (are yout OK with using a terminal or should I give some more details?.)

make a directory where you want your pv2devkit thing:
mkdir pv2devkit
cd pv2devkit 

to tell cvs what it is you want you need to set and environment variable, in this case its the one called  "CVSROOT"
according to the link you gave and it being on sourceforge the thing you want is this:

```
export CVSROOT=:pserver:anonymous@cvs.sourceforge.net:/cvsroot/pv2devkit
```

that basically tells the sourceforge server you want to log in as an anonymous user to check out some free thing. otherwise you would need a username and password. If you are anonymous and it asks for your password just slap enter.

now from your website link you see a number of directories or files for this pv2devkit project.

one of them is called pvtool-for-linux... that looks like the one you want.

so now that CVSROOT is set you want to "check out" the project called pvtool-for-linux. basically all this does is copy the pvtool-for-linux directory from sourceforge.net to your pc. the straight way to do it is:

cvs -z3 co pvtool-for-linux

in english thats cvs "with zip compression level 3" "check out" pvtool-for-linux

i had to do that a couple of times before it worked, since I'm anonymous I'm on the bottom of the food chain so I am not guaranteed the best acces to sourceforge.

if you type ls now you will see the directories it copied

now i can:
cd pvtool-for-linux
ls

i see all the files, and some sourcecode files, but I have no idea how to compile this.
normally you just type:
configure
make
install

there are two files with extension .sh which are shell scripts  and to run win32.sh:
./win32.sh 

but that gives me some errors.
"make" also gives errors.

maybe someone who understands this can help you further...

---

### Post by RAOF on 2005-11-28
I've had a browse of the CVS, and there doesn't appear to be any sort of help-type file there, nor any of the other files (autogen.sh, configure) that normally accompany the CVS source of a program.  So, they're doing something different.  

What does the homepage have to say about installing this software?  That should be your first port of call.

Stepping back for a second, what is it that this program does?  Rather than trying to install this particular program, could there be another program that would work for you, and is in the Ubuntu repositories?

---

### Post by %hMa@?b&lt;C on 2005-12-04
i cant get the file. i know that you need libusb which i already have.

---

### Post by %hMa@?b&lt;C on 2005-12-04
alright, i have got the file, now... i cant do make or makefile

---

