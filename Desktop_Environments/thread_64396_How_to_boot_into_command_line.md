---
title: "How to boot into command line?"
date: 2005-09-10
forum: Desktop Environments
---

### Post by loafofbread34 on 2005-09-10
Hi,
I would like to be able to boot into command line as default. (E.G. never start X Windows.) So i can telnet and stuff.

Thanks.

---

### Post by aquaboot on 2005-09-10
Well,

You should be able to modify your /etc/inittab file: sudo nano /etc/inittab

# The default runlevel.
id:2:initdefault:

by replacing "2" with "3".  This will boot you into multiuser non-graphical mode after restart.  You can also just try it out from an x-term by running the "init" (initialization level) command on an x-term:

sudo init 3 <enter>

Let me know how it goes.

-aquaboot

---

### Post by aquaboot on 2005-09-10
ps-  you should be using ssh (secure shell) instead of telnet (much more secure this way).  You can always telnet or ssh through xwindows with an x-terminal. ;-)

-ab

---

