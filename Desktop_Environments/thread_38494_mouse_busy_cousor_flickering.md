---
title: "mouse busy cousor flickering"
date: 2005-05-31
forum: Desktop Environments
---

### Post by equivsys on 2005-05-31
I have just installed Horay and I must say it is fantastic, what an easy install compared to many of the other distros.  I am having one really annoying problem though.  I have been searching around for an answer to no avail.

The mouse coursor flicker rapidly whenever it goes into the "busy circle" or the "busy circle with pointer".  My horizontal and vertical refresh rates in xorg.conf are right out of the company's spec sheet and I don't have problems with any other animation. 

Thanks in advance.

---

### Post by equivsys on 2005-06-02
It seems as if this may be a nvidia driver problem.  When I run X with the nv driver instead I do not get the problem of the animated cursors flickering.  However, I run a dual head system and since nv doesn't support this I need to use the nvidia driver.

Has anyone else had/fixed this bug or know if this is indeed a nvidia bug.

---

### Post by equivsys on 2005-06-02
Alright I figured it out...  The current nvidia driver requires that you add 

Option "HWCursor" "0"

to the device section of xorg.conf.  This will get rid of any flickering of animated Xcursors.

---

