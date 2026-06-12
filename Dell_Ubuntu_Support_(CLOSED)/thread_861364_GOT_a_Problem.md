---
title: "GOT a Problem"
date: 2008-07-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by linux guy #5 on 2008-07-16
HI im having a problem with ubuntu when i boot. this is the error i get Busybox v1.1.3 (debian 1:1.1.3-5ubuntu12) built in shell (ash) enter help for a list of built in commands.

initremfs 

HELP NEEDED 

if anybody wants to know how i wrote this im using xp right now

---

### Post by gbrainin on 2008-07-16
The error indicates that Ubuntu can't properly mount the hard drive partitions.  Solving this may be as simple as adding a parameter to your boot line, but you'll need to provide a little more information.  For example:

What kind of computer are you using?
What version of Ubuntu?
How did you install it?  That is, did you put it on a separate partition or are you using Wubi?

There may be other things I'm not thinking of, but that'll get you started.

---

### Post by smo0th on 2008-07-17
> **linux guy #5 said:**
> HI im having a problem with ubuntu when i boot. this is the error i get Busybox v1.1.3 (debian 1:1.1.3-5ubuntu12) built in shell (ash) enter help for a list of built in commands.

initremfs 

HELP NEEDED 

if anybody wants to know how i wrote this im using xp right now

here's what you need to do:

from your xp, open cmd and type ```
chkdsk /f d:
``` assuming drive d is where you installed your wubi. Reboot and you should be able to use ubuntu again :)

---

### Post by linux guy #5 on 2008-07-17
Thanks it Ubuntu works now:)

---

### Post by linux guy #5 on 2008-07-17
Thanks Ubuntu works now:)

---

### Post by smo0th on 2008-07-17
good to know, enjoy :D

---

