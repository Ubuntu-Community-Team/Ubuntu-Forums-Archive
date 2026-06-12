---
title: "Windows fragmenting on my dual boot"
date: 2008-04-19
forum: Desktop Environments
---

### Post by maaylix on 2008-04-19
Here is the situation:

I have two 80gig SATA hard drives

The first one has two partitions: Windows XP NTFS and Ubuntu (7.10) root

The second has a small NTFS partition that I use as cache space for Windows, and the rest is my
ubuntu home partition

The Problem:

I like to listen to music while using XP and Ubuntu, To do that, I left all my mp3 files on my main XP partition
as windows doesn't read the Ubuntu partition while Ubuntu can read NTFS.

Thing is that I've been noticing that my windows partition has been fragmenting a lot more than it did when I used to have only XP installed. Also, I get alot more erros in scandisk after prolonged use of my pc

So I'm thinking that Ubuntu isn't doing my Windows Xp partition very good when it writes or reads files from it

Finally, I was thinking about doing yet another partition, a FAT32 partition to keep files that I use in both OS'es

Dose Ubuntu handle FAT32 better than it dose NTFS, or will my FAT32 partition be as fragmented as my current NTFS?

---

### Post by leo_rockway on 2008-04-19
I'd say that GNU/Linux handles Fat32 a lot better, but I have no scientific proof in which to base this.

It's just that ntfs-3g working state is pretty recent and Fat32 has been around a lot longer.

---

