---
title: "Trying to install gcc"
date: 2009-02-25
forum: General Help
---

### Post by JBudOne on 2009-02-25
Hey guys, I've been trying to install gcc 4.1 on Ubuntu, and I've been running into so many problems X_x I think it's about time to start asking for help.

So I need, specifically, gcc 4.1.x, so I got 4.1.2. I already have gcc 4.3 installed, is that a problem at all? Anyways, I ran the package manager and it showed this error, "Error: Dependency is not satisfiable: gcc-4.1-base"

I looked around on google for this and read up that all I have to do is go into Terminal and type: dpkg --force-depends -i gcc-4.1_4.1.2-23ubuntu3_i386.deb   .. After trying this I get this error, "dpkg: requested operation requires superuser privilege".

So I tried using su to login, still the same error. I read around and heard that I should try this: sudo dpkg --configure -a   ... After trying that, and putting in my password, I tried the dpkg again and still the same error pops up. 

Lastly I read that I can just open up the Synaptic Package Manager, and click "Fix Broken Packages", then try opening it again.. This didn't work either, I'm pretty sure it couldn't even find the package (which is on my desktop). 

Does anyone have any ideas? I'm a complete Linux noob X_x so I'm ready for it to be something really embarassingly obvious or something. Thanks =]

---

### Post by taurus on 2009-02-25
Do you really need to use version 4.1.2 instead of 4.3?  GCC depends on a bunch of other files so downloading gcc-4.1_4.1.2-23ubuntu3_i386.deb will cause it to complain about the dependencies.  Otherwise, try removing the current version that you have on your machine first and see if you can install the older version.

```
sudo apt-get remove build-essential
```

---

### Post by Yellow Pasque on 2009-02-25
Why do you need gcc 4.1? Programming classes?

---

### Post by JBudOne on 2009-02-25
Hey guys =] Thanks so much for the replies, I'm trying it out right now - I'll tell you how it goes. I do need gcc 4.1 to compile Wolfenstein: ET, an old game made by ID (I was told you can only compile it with gcc 4.1.x).

---

### Post by JBudOne on 2009-02-25
So I tried removing the current gcc version, and it did delete a lot of other essential files.. It got to the point that all the letters turned to squares, a bunch of graphics were suddenly gone, the windows all changed and the whole thing was pretty much screwed =P so I just deleted and made a new VM with Ubuntu in it again. Is there any other way I can delete these files so that I can install the older gcc? Or perhaps have 2 versions of gcc installed at the same time? Thanks.

---

### Post by taurus on 2009-02-25
The build-essential package is not a default installed package.  Therefore, you have to install it yourself if you want to compile something.  Again, if you want to install an older gcc compiler, you need to hunt down all the dependencies for it.

Have you at least tried to compile Wolfenstein: ET with the newer gcc?

---

### Post by JBudOne on 2009-02-27
Hey guys =] Thanks for the help, I finally compiled it. Apparently I was trying to compile it the wrong way, you're supposed to use scons which I guess calls gcc itself, so it did end up working with the newer gcc.

---

