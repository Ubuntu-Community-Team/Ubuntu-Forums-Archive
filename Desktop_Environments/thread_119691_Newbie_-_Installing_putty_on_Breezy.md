---
title: "Newbie - Installing putty on Breezy"
date: 2006-01-20
forum: Desktop Environments
---

### Post by Wagawaga on 2006-01-20
Another Linux Newbie -- Hi, I am trying to install putty on Ubuntu 5.01 Breezy -- When running make -f Makefike.gtk, I get the following errors -- /bin/sh: gtk-config: command not found & /bin/sh: cc: command not found -- please help!:confused:

---

### Post by jscrilla on 2006-01-20
I'm a newbie too, but I think I can answer this sufficiently. If you open a terminal window and type the following it should install Putty for you. 

$sudo apt-get install putty

Hope that helps!

---

### Post by prammy on 2006-01-20
any particular reason you use putty?

if you just want to ssh in to a machine, you can do so from the command line 

example:
ssh username@host

---

### Post by darth_vector on 2006-01-20
cc is a c compiler. you can get this with```
sudo apt-get install build-essential
```
but like prammy said, ssh is installed by default and its good.

---

### Post by Wagawaga on 2006-01-20
Thanks - I'm using putty as a Terminal emulator to connect to Sco-Openserver P.O.S system...

---

