---
title: "Question about runlevel..."
date: 2005-06-23
forum: Desktop Environments
---

### Post by kimes on 2005-06-23
I'm currently using ubuntu hoary..
when I check runlevel with 'runlevel'command..

It tells me that '2'
Ok I see I'm currently in runlevel 2..

I guess when boot up.. It's run level 0
right?

and go to the 2 and finally get to the 2 which I'm currently in..

My question is.. what is done when we are in runlevel 0 and 1?

and which controls transfering from one runlevel to another runlevel?

---

### Post by rachii on 2005-06-23
runlevel 0 is shutdown, runlevel 6 is reboot.   in ubuntu runlevels 2-5 are all the same, unlike maybe if your familiar with, fedora etc... 
2-5 being multi-user
and 1 being single-user

you can control what level you are in.  default is two (as you've noticed)  you can change this in /etc/inittab
or if you type ```
sudo init #
``` it will set to that runlevel

---

