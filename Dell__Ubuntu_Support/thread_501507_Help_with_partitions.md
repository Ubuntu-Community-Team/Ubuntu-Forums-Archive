---
title: "Help with partitions"
date: 2007-07-15
forum: Dell  Ubuntu Support
---

### Post by yomama07024 on 2007-07-15
I have Ubuntu burned on a disc.  I have Windows installed on my computer.  Is there a way I can set up dual boot for Ubuntu without erasing my files on Windows?  I have 7 MB in the free space partition and the rest is for my Windows partition.  Are my Windows files going to be deleted?  If not, how can I set this up?

---

### Post by dreadlord_chris on 2007-07-15
> **yomama07024 said:**
> I have Ubuntu burned on a disc.  I have Windows installed on my computer.  Is there a way I can set up dual boot for Ubuntu without erasing my files on Windows?  I have 7 MB in the free space partition and the rest is for my Windows partition.  Are my Windows files going to be deleted?  If not, how can I set this up?

7MB is not even close to enough space to install Ubuntu, or any other OS except maybe DOS3.1...
Anyway - here's a guide on dual-booting Windows & Ubuntu:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by yomama07024 on 2007-07-15
Is it possible for me to take some free space from my partition that I am using for Windows, and add it to the free space partition?

---

### Post by dreadlord_chris on 2007-07-16
> **yomama07024 said:**
> Is it possible for me to take some free space from my partition that I am using for Windows, and add it to the free space partition?

yes it's possible:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Jkane13 on 2007-07-16
I did this.  The windows resize feature wouldn't free up much space.  Seems like it likes to put non-movable files near the end of the free space.  :-(  I ended up booting from the Ubuntu CD and then running the gparted utility.  It was scary, but it did resize the windows partition much smaller and freed up most of the disk for Ubuntu to load on.  On my next boot into Vista, it ran a disk fix program for a while, but all seemd fine after that.

No guarantees you will have as much luck!

---

### Post by strabes on 2007-07-17
Glad you got it working. It is scary the 1st time but once you get it working it's great.

---

