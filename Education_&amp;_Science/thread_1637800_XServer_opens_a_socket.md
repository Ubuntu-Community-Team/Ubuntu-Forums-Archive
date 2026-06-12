---
title: "XServer opens a socket?"
date: 2010-12-04
forum: Education &amp; Science
---

### Post by Kralizec on 2010-12-04
I have an assignment for my operating systems class that asks me to implement a rudimentary security system by modifying the system calls that allow for socket connections to disallow all ports except specifically allowed ones.

   After (hopefully) implementing this, when I reboot my virtual machine (my working environment) I get for a GUI only a black screen with an X in the middle, indicating to me that my changes have blocked the X server from connecting to some port. (Currently my changes have only been implemented on the connect() system call.)

   Can anyone shed any light on the X server and its port connections for me?

Thanks!

---

