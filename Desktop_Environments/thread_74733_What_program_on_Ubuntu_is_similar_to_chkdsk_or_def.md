---
title: "What program on Ubuntu is similar to chkdsk or defrag from Windows ?"
date: 2005-10-12
forum: Desktop Environments
---

### Post by kurtkraut on 2005-10-12
Hi,

I'm a very worried about the health of my data in my hard disk. Windows has easy tools to check and solve block errors (**chkdsk**) and a defragmentation tool (**defrag**) that speeds up a lot the computer.

How could I do these maintenance  on Ubuntu ? Is there anything beyond checking blocks en defrag ?

---

### Post by Dolphin on 2005-10-12
These are things you don't need to worry about with EXT3 partitions.  There ARE one or two defragging utilities for Linux out there, hell if I can remember what they are.  But there's alot of debate as to how effective or necessary these utilities are.  EXT3 is naturally "resistant" to fragmentation.  You could run it for a year and still only see maybe 1% fragmentation, which is fine.

Stop thinking in microsoft terms. :p

---

### Post by aysiu on 2005-10-12
You don't need to defrag.

---

### Post by Olav on 2005-10-12
You don't need defrag in Linux. And the general health of your file systems is checked regularly at startup. If something is found wrong you won't miss it. Cool huh?

---

### Post by mo_x on 2005-10-12
You can use fsck to check the file system. Check out the man page.```
man fsck
```

---

### Post by Olav on 2005-10-12
[QUOTE=mo_x]You can use fsck to check the file system. Check out the man page.[/QUOTE]
Yes, but then read it GOOD. You can do lots of damage with fsck. Normally, you don't ever need it.

---

### Post by wylfing on 2005-10-12
Agreed. Don't advise newbies to run fsck :) 

Your disks are checked automatically every reboot. Don't worry about it.

As was already stated, degragging is something you do on Windows because Windows file systems have a problem with fragmentation. The file systems commonly used on Linux do not suffer from fragmentation, so defragging is not required.

---

### Post by Leif on 2005-10-12
I think a safe way of checking your disks can be done by specifying it for the next boot (no mess fsck'ing mounted partitions this way) :

sudo shutdown -Fh now

to turn off your computer, and have it checked at boot.

---

### Post by wylfing on 2005-10-12
Pretty good advice. I understand the -F option, but why -h? That'll cause the machine to power off, no?

---

### Post by super on 2005-10-12
ya, the 'h' is for halt. as opposed to 'r' which is for reboot.

---

### Post by kurtkraut on 2005-10-12
Hi,

Some good points were stated here. I suggest that these considerations should be added in Ubuntu's wiki or other availuable FAQs. This is a good example of Ubuntu superiority while comparing to Windows and it should be told to Windows users.

Thanks a lot.

---

