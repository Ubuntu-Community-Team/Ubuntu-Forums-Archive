---
title: "problem with the ut2004 demo"
date: 2006-07-19
forum: Gaming &amp; Leisure
---

### Post by MakLeod on 2006-07-19
I installed the ut2004 demo and everything seemed to install just fine.  Now when I go into the ut2004demo folder I cannot find the file I need to start the program up.  All the directory contains is the various file folders (sounds, graphics etc) and a ut2004-demo.sh file, and an .xpm file.  I am also using the 64 bit version of Dapper if that makes any difference.  The .sh file is only 1.2kb, so that can't possibly be the main opening file right?  Thanks in advance.

---

### Post by goobers on 2006-07-19
you should just be able to type either **ut2004** or **ut2004-demo** in the console. if not, try putting **sh** first

---

### Post by MakLeod on 2006-07-19
sorry to sound so noobish, but is the console the same thing that comes up after typing alt+f2?

---

### Post by tuxcantfly on 2006-07-19
yes, but you don't get any output like that. for a full console, on ubuntu go applications- accessories- terminal or in kubuntu go kmenu- system- konsole

---

### Post by Shay Stephens on 2006-07-19
When I installed it, it made an icon in the acessories - games menu

---

### Post by MakLeod on 2006-07-19
just navigated to the directory using the terminal and tried to execute the .sh file and got this:

macleod@jedd:/tmp/ut2004demo$ sh ut2004-demo
./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by goobers on 2006-07-19
try this- in a terminal type

```

sudo apt-get install libstdc++6

```
then try to run it

---

### Post by goobers on 2006-07-19
actually, that version of the library seems to be this

```

sudo apt-get install libstdc++5

```

do both just to be sure ;-)

---

### Post by MakLeod on 2006-07-19
argh, says i have the updated version

macleod@jedd:~$ sudo apt-get install libstdc++6
Reading package lists... Done
Building dependency tree... Done
libstdc++6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
macleod@jedd:~$

---

### Post by MakLeod on 2006-07-19
actually got it to work because i didn't have the ++5 ones installed.  thanks so much!

---

### Post by goobers on 2006-07-19
no problemo :)

---

