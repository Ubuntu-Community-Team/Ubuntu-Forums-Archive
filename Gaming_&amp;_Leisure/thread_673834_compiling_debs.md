---
title: "compiling debs"
date: 2008-01-21
forum: Gaming &amp; Leisure
---

### Post by pibb69173 on 2008-01-21
ok i need help on compiling a deb  package for a game called rigs of rods thy only provide a tarball download so if someone could either walk me step by step or plz make a deb package thanx (p.s. rigs of rods is easy to find just google it)

---

### Post by Lord Illidan on 2008-01-21
Do you know how to compile software from source, not neccessarily making a deb package?

---

### Post by pibb69173 on 2008-01-21
not really im sort of a noob and im still learning

---

### Post by DarkSim on 2008-01-21
Here is an easy tutorial (with pics and .gifs) for source compiling. If you do the package manager install method  you end up with a .deb package in the source folder. Thats how I make my .debs for later use.

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by pibb69173 on 2008-01-21
i dont think the released the source code for rigs of rods

---

### Post by stuart.crouch on 2008-01-22
From their FAQ -

Is it really free? What license is it under?

RoR is a free, closed source program, aka freeware. All rights are reserved to its author. In return, you agree that if you create a vehicle for RoR the author can include it in the official release, all credits given. The source code is kept closed for many reasons, one of which is that RoR is coded in a difficult to maintain, proof-of-concept way, not suitable for collaborative coding, another reason being the risk of seeing the code and ideas stolen by the game industry. 

In other words, he hacks and doesn't follow good coding practice ;) and likes the idea of selling his idea to the game industry at a later stage...
But in summary, no he doesnt give out the code (but he does want your stuff which is in a format he can fully read!)

I just downloaded the tar.gz file from the RoR homepage to my windows PC at work.  It looks like you extract the folder to somewhere in your home directory, change to that folder using the terminal and run it using ./RoR

---

### Post by pibb69173 on 2008-01-22
i did but it gave me a shared librarys error

---

### Post by pibb69173 on 2008-01-22
it wont let me open any thng i get error

when i try to open ./RoR it says ./RoR.bin: error while loading shared libraries: libIL.so.1: cannot open shared object file: No such file or directory

---

### Post by Cappy on 2008-01-22
Use
```
sudo apt-get install libdevil1c2 libmng1
```

Getlibs can install all missing libraries for you if you have any more:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by pibb69173 on 2008-01-23
frikin A 

it gave me an object error

error while loading shared librarys:libCg.so: cannot open shared object file: No such file or directory

---

### Post by reidbold on 2008-01-31
You need the nvidia cg tool kit
[www.nvidia.com/object/cg_toolkit.html#downloads]("http://www.nvidia.com/object/cg_toolkit.html#downloads")

a few more adventures await, but if you have made it this far you'll be ok. you have to copy libtiff and libopenal, just copy & rename the ones install on your system.

---

