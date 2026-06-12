---
title: "kernel updates break resume from suspend/hibernate"
date: 2008-11-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ethanay on 2008-11-28
hi all, 

apologies if someone is covering this issue already, but i searched and couldn't find anything:

dell xps m1330 running hardy 8.04

kernel 2.6.24-19 has worked relatively flawlessly for me, except for a few very minor glitches here and there.

more recent kernel versions 2.6.24-21 and -22 cause all sorts of problems when i try suspend/hibernate:
1. hang on suspend
2. hang on resume (console switching helps sometimes)
3. disabled networking on resume
4. compositing problems
5. no more taskbar hardware monitoring (hard disk monitoring fails to work at startup)

a few debug messages seem to indicate a conflict between the suspend/resume commands and the wireless driver.

has anyone else had any of these issues?  i've searched launchpad and couldn't find someone discussing either kernel update in terms of breakage or regression.

but until i find out what it is, it essentially makes the new kernel versions unusable for me

---

### Post by ethanay on 2008-12-05
rrrreally?  no one else had problems with the kernel upgrades past 2.6.24-19?

---

### Post by Denny Johnson on 2008-12-06
If you have not seen this:

[http://ubuntuforums.org/showthread.php?t=829869&page=3](http://ubuntuforums.org/showthread.php?t=829869&page=3)

 it helped me w a similar problem.

---

### Post by ethanay on 2009-01-01
Thanks for the suggestion -- the thread and solutions therein isn't relevant to this problem...although it has helped other problems (network occasionally fails after resume)

This post
[http://ubuntuforums.org/showpost.php?p=6306310&postcount=6](http://ubuntuforums.org/showpost.php?p=6306310&postcount=6)

seems to describe problems similar to those i am experiencing

---

### Post by ethanay on 2009-01-14
This problem appears fixed in the latest kernel update: 2.6.24.23

:guitar:

---

