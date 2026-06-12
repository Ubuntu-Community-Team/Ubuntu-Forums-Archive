---
title: "Grub Menu Issue"
date: 2010-01-20
forum: Desktop Environments
---

### Post by l2e on 2010-01-20
I am running a Minimal installation of Karmic that I installed yesterday and it periodically freezes on startup at:
 
*Loading LIRC Modules
lirc-0.8.6[774]:lircd(default) ready, using /var/run/lirc/lircd
 
It will sit there until I turn it off and on again.  However, upon turning it back on, I get the Grub 2 menu and it does not auto load the defaul OS.  I have to use the keyboard to press enter to select the OS I want to load.  The problem is the machine is my HTPC with no keyboard or mouse attached, only a remote.  Is there a way to set Grub 2 to auto load the default OS in this case just like it does on a normal boot?
 
Remember, the Grub 2 menu only shows and doesn't go away if I have to turn the power off and on due to startup hanging at LIRC.
 
BTW, this only started happening with 2.6.31-17 as the Minimal install of Karmic that I did 2 weeks ago does not have this problem and this new LIRC hanging problem has shown itself on all installs I have done starting yesterday.

---

### Post by meierfra. on 2010-01-20
Try this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail)

---

### Post by l2e on 2010-01-22
Excellent!
 
That fixed the problem.

---

### Post by meierfra. on 2010-01-22
> That fixed the problem.

Great. And good luck with your freezing problem.

---

