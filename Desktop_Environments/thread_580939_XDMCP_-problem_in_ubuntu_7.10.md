---
title: "XDMCP -problem in ubuntu 7.10"
date: 2007-10-19
forum: Desktop Environments
---

### Post by mokkai on 2007-10-19
already my version is ubuntu 7.04....
in that i can open XDMCP and connect with other system....

just now i installed latest ubuntu version (7.10)
my XDMCP is not working...
when in login screen window...
Options-->Remote Login via XDMCP
i can see the list IP addresses if i click that corresponding IP address
and connect ,
then my system going to connect and show some messages within a second(so i can't see the Error messages) and came to my original login page

how to solve this ?
how to see the error messages ?...

but i can connect that system through SSH ..

---

### Post by nickmcg on 2007-10-19
I have the same problem, and it appears to be a problem with 7.10 login.

From my Feisty (7.04) machine, I can remotely connect to both 7.04 and 7.10 systems, but I cannot connect to either from a Gutsy system.

I also cannot find any error messages (maybe I'm looking in the wrong place!)

Nick

---

### Post by bihe on 2007-10-19
same for me - unfortunately

@otherthread
[http://ubuntuforums.org/showthread.php?t=581111&highlight=gutsy+xdmcp](http://ubuntuforums.org/showthread.php?t=581111&highlight=gutsy+xdmcp)

@launchpad
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/150193](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/150193)

---

### Post by Marcel Meijer on 2007-10-23
I just bypassed the problem by selecting:
System -> Administration -> Login Window -> Tab Remote style plain (the third choice)

This option gives me a login window on my terminal client Cygwin/X.

---

### Post by dizm on 2007-11-01
doesn't work for me.  feisty trying to access gutsy over xdmcp (enabled with plain).

---

### Post by dgrafix on 2008-02-18
Same problem here,

I connect then after a few secnds it returns to the main login

---

