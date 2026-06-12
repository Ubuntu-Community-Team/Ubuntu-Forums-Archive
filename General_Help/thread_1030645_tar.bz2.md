---
title: "tar.bz2"
date: 2009-01-04
forum: General Help
---

### Post by RedSingularity on 2009-01-04
Hey guys, i need some help with this tar.bz2 file i have.  I am trying to install it and when i do i get the following message: 

```
make: *** No targets specified and no makefile found.  Stop.
```

And the make install

```
make: *** No rule to make target `install'.  Stop.
```

Please help....

---

### Post by logos34 on 2009-01-04
what's the file exactly and did you unzip it?

---

### Post by RedSingularity on 2009-01-04
The file is Tight VNC.  I dont beleive it is in the repositories.  And yea i unziped it to the desktop.  I did not unzip it with the terminal though.  I just right cliked the file and then unziped it.

---

### Post by shecky on 2009-01-04
TightVNC is in the repos.
```
sudo apt-get install tightvncserver xtightvncviewer
```

If you really want to compile it, you have to cd into the unarchived directory before using make.

Edit: I just downloaded the TightVNC source, and it's not a standard make/make install deal. Thoroughly read the README file for installation instructions.

---

### Post by RedSingularity on 2009-01-04
Ah perfect!  Thanks!  :)

---

