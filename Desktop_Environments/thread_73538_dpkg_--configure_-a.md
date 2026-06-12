---
title: "dpkg --configure -a"
date: 2005-10-09
forum: Desktop Environments
---

### Post by augereffect on 2005-10-09
Whenever I try anything with synaptic, or try to run the update program, or use apt-get or anything of that nature, I get this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Running this command causes my computer to crash, after a few minutes of doing its thing.  Any ideas?

---

### Post by cwaldbieser on 2005-10-09
[QUOTE=augereffect]Whenever I try anything with synaptic, or try to run the update program, or use apt-get or anything of that nature, I get this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Running this command causes my computer to crash, after a few minutes of doing its thing.  Any ideas?[/QUOTE]
Well, the command it is telling you to use is supposed to configure and unpacked but not installed packages.  That means it will run the post-install scripts for those packages, one of which is likely to be what is crashing your computer.

Your best option is probably to purge the packages that were not fully installed-- any idea what they might be?

---

