---
title: "Ubuntu 7.04 on Dell Inspiron 1520"
date: 2007-09-29
forum: Dell  Ubuntu Support
---

### Post by damonjablons on 2007-09-29
Hi, this is probably a simple problem, but I followed the forum tutorial on how to get ubuntu 7.04 working on a Dell Inspiron 1520.  The problem is that now, every time i restart ubuntu, all of the settings i made before I restarted are lost!

for instance, I've changed my resolution to 1280x800.  but when I restart, it will be set back to 1024x768.

or, whenever I start firefox, it pops up the usual boxes asking me if i'm sure i want to view an encrypted page and what not.

please help me fix this issue.  I'm brand new to linux, and i don't want to submit to mr. gates anymore.

---

### Post by linux23dragon on 2007-09-29
> **damonjablons said:**
> Hi, this is probably a simple problem, but I followed the forum tutorial on how to get ubuntu 7.04 working on a Dell Inspiron 1520.  The problem is that now, every time i restart ubuntu, all of the settings i made before I restarted are lost!

for instance, I've changed my resolution to 1280x800.  but when I restart, it will be set back to 1024x768.

You need to modify the xorg.conf file.  
Can you please send 

Can you open up a terminal and copy past this command:-
```
cp /etc/X11/xorg.conf ~
```
And post the xorg.conf found in your home directory please? 

> **damonjablons said:**
> 
or, whenever I start firefox, it pops up the usual boxes asking me if i'm sure i want to view an encrypted page and what not.
That  normal operation

> **damonjablons said:**
> 
please help me fix this issue.  I'm brand new to linux, and i don't want to submit to mr. gates anymore.

Welcome to Linux.  Were you are about to learn that there is a Operating System design difference (compared to Windows).  It is one of the many reasons why Linux does not have the typical security or user limitations that Windows has.

---

