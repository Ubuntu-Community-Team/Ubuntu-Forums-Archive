---
title: "missing /usr/X11R6/include/X11/Xlib.h"
date: 2009-02-17
forum: General Help
---

### Post by ones3k2 on 2009-02-17
I am compiling a project at work and receive this error: /usr/X11R6/include/X11/Xlib.h: No such file or directory

I am running Ubuntu 8.10 and I have tried installing many packages to correct this. I have installed libx11-dev and xorg-dev but I still receive the error.

What have I missed?

---

### Post by StOoZ on 2009-02-17
hmmm... I know its usually under 
/usr/include/X11/Xlib.h

---

### Post by ones3k2 on 2009-02-18
bump

---

### Post by StOoZ on 2009-02-18
a symbolic link in '/usr/X11R6/include/X11/' which points to /usr/include/X11/Xlib.h  might do the job , I guess.

---

### Post by ones3k2 on 2009-02-18
> **StOoZ said:**
> a symbolic link in '/usr/X11R6/include/X11/' which points to /usr/include/X11/Xlib.h  might do the job , I guess.

that worked! THANKS!

---

### Post by _dino_ on 2009-05-16
Hi Guys,
I am running Ubunto Desktop 9.04 and I am unable to locate my Xlib.h file which is supposed to be under usr/X11R6 directory.
I tried looking under other directories as well and searching for it using locate or find command but withotu success.
Anyone knows how to add X11R6 to my system so I can compile my programs.
Thanks

---

### Post by snakeman on 2009-05-29
apt-get install libx11-dev

should do it,



snakeman

---

### Post by iansane on 2009-10-15
I came across this post while looking for my x11 header files. 

The x11R6 folder is full of executables and a looping x11 link that points to it's self. no .h files in there at all.

Libx11-dev is installed on my system and in the package properties>installed files is a very short list of header files. They are where I would think they should be, in the usr/include/x11 

the correct path for xlib.h on my Hardy system is /usr/include/x11/xlib.h 



Can this not be downloaded as a library like downloading the c++ standard library?

I'm a beginner and tried following a supposedly simple how to to get started but there's no mention in the how to of where the included .h files are and the includes in the example code were wrong for my system.

I think it's a good idea to copy all the libraries into one place and organize them a bit and then use that directory for compiling. Seems like that's  what the usr/include folder is supposed to be but it's starting to get a little cluttered and disorganized with loose .h files that aren't even in a subdirectory. Don't know if that means they are specific to Ubuntu since they are just in the include folder?

You just have to look around for them.

---

### Post by Cali_U on 2010-03-24
I'm new to Ubuntu,and I can't find Xlib.h.

I already installed libx11-dev (or at least tried to, I'm pretty sure it worked).

Any help?

Is it possible it's somewhere and I just can't find it?

---

### Post by ruehli on 2011-01-24
> **Cali_U said:**
> I'm new to Ubuntu,and I can't find Xlib.h.

I already installed libx11-dev (or at least tried to, I'm pretty sure it worked).

Any help?

Is it possible it's somewhere and I just can't find it?


I am also looking for /usr/X11R6/include/Xm. So far I could not find a solution for Ubuntu 10.04

---

