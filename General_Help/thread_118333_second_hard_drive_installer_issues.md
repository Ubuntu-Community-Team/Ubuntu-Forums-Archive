---
title: "second hard drive installer issues"
date: 2006-01-16
forum: General Help
---

### Post by the_padawan on 2006-01-16
Hey all, 

I just installed kubuntu 5.10 i386 on my desktop machine. 

I figured I'd make sure this is known:
Installation was rougher than it should have been; the installer kept stalling at one step. After choosing which partition to overwrite, the installer would either get trapped at a blue screen or display a message claiming it was "starting the partitioner" which hung at 52%. The ctrl+alt+F3 console said the installer was "Reading all volumes." After a few failed attempts with this result, I disconnected my second hard drive, a 160Gb with 6 FAT32 partitions, and installation worked fine.

Now that I have the system up and running I have reconnected the slave drive and can access it by mounting /dev/hdb#.

So I have no idea what went wrong. Since then, however, I've found ku to be an excellent and very friendly distro and I look forward to working with it as my main desktop.

---

