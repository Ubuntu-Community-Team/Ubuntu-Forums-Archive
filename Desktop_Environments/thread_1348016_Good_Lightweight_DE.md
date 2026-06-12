---
title: "Good Lightweight DE"
date: 2009-12-06
forum: Desktop Environments
---

### Post by LIB53 on 2009-12-06
So i took out an old laptop and installed minimal ubuntu just for fun. Now i kind of think having a desktop environment might be a bit more useful.

Given these specs:

Pentium 2 366MHz
128MB RAM
7GB HDD
1x CD-ROM

What desktop environments can i install? Which would be the best idea for this ancient machine?

---

### Post by SavannahMudPuppy on 2009-12-06
You might want to try Puppy Linux.  ;)
 
[http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm](http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm)

---

### Post by wilee-nilee on 2009-12-06
> **LIB53 said:**
> So i took out an old laptop and installed minimal ubuntu just for fun. Now i kind of think having a desktop environment might be a bit more useful.

Given these specs:

Pentium 2 366MHz
128MB RAM
7GB HDD
1x CD-ROM

What desktop environments can i install? Which would be the best idea for this ancient machine?
 
You might try lxde, since you have the minimal installed but the puppy option will run much faster.
[http://puppylinux.org/wikka/Puplets?show_comments=1](http://puppylinux.org/wikka/Puplets?show_comments=1)

---

### Post by ArgentStar on 2009-12-06
You could try the [Haiku BeOS]("http://www.haiku-os.org/").  I know it's not Linux, but it's a desktop environment that should run on those kind of specs.  It is still in alpha, however, and can't set up its own partitions.  So you'll need to use an Ubuntu Live CD or something to set up a bfs partition before running the Haiku Live CD.

---

### Post by akashiraffee on 2009-12-06
Okay, I could find much out about "minimal ubuntu" on google -- do you mean an install with no X at all?

Just to get this straight --** the DE is not the Graphical User Interface.**  It is a top heavy component layer built on it.

You do not need any DE at all in order to run X windows.  You pretty much do need a window manager -- witness, DE's have a window manager that they use.  Like, the default WM for gnome is metacity.  But metacity is built to work with a DE, I don't think it's much good on it's own.

Generally, "standalone" window managers run with much much fewer resources than a DE but they provide almost the same thing (menus, windows, taskbars, etc.)  FVWM2 is a standalone window manager that provides a lot of functionality with no DE, there are more than a few others I think.

---

### Post by LIB53 on 2009-12-06
Alright, i'm downloading puppy linux right now and when i installed LXDE (sudo apt-get install lxde) it installed but would freeze when it got to GDM. I was thinking about trying again though with fvwm crystal. Any insight on that?

And here you go for the minimal install info: [https://help.ubuntu.com/community/Installation/SystemRequirements#Absolute%20minimum%20installation](https://help.ubuntu.com/community/Installation/SystemRequirements#Absolute%20minimum%20installation)

---

