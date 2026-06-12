---
title: "Doom3 Install problem on x86_64 Feisty 7.04"
date: 2007-04-23
forum: Gaming &amp; Leisure
---

### Post by RawMustard on 2007-04-23
I Just got my 64bit-feisty all working how I want, so I tried to install doom 3.  I tried doom3-linux-1.3.1302.x86.run package first and got the same error, so I downloaded the latest version thinking perhaps my copy was corrupted in some way and I still get the error - checksums are fine btw!  Anyone might have a clue where to start solving this problem?

It doesn't seem to be decompressing?
It is suppose to run on amd64 arch.

me@the-matrix:~$ sudo ./doom3-linux-1.3.1.1304.x86.run
Verifying archive integrity... All good.
Uncompressing DOOM 3.............................................................................................
./setup.sh: 279: /home/me/.setup14014: not found
./setup.sh: 290: /home/me/.setup14014: not found
me@the-matrix:~$

---

### Post by lakersforce on 2007-04-23
I would recommend you take a look at this thread: [http://ubuntuforums.org/showthread.php?t=416871](http://ubuntuforums.org/showthread.php?t=416871)

---

### Post by RawMustard on 2007-04-23
Thanks, that fixed that problem.  Now to make him run #-o

---

