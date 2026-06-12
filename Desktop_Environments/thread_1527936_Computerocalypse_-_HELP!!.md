---
title: "Computerocalypse - HELP?!?!?"
date: 2010-07-09
forum: Desktop Environments
---

### Post by nibblet5109 on 2010-07-09
Hi again.  I dunnit this time... I was using GParted Live to resize my Windows XP partition on my desktop aaaaand... it rebooted properly and now says "no such partition" and won't boot from anything. It doesn't even recognize my dell utilities partition. I can boot to the GParted Live disk - and that is all.  So I'm relatively certain that I just destroyed something... anyone wanna help me either fix it or get ANY OS back up and running? Would be appreciated.


if you're gonna break somethin... don't half@$$it!!!

---

### Post by nibblet5109 on 2010-07-09
An update - I got it to boot from a 10.04 live disk. investigating. still need help.

---

### Post by nibblet5109 on 2010-07-10
Another update.... and if you know I'm bleeping something up hardcore - please stop me asap. i'm checking this thing on a minutely basis.

First I deleted the old Ubuntu partition with my GParted Live CD being my boot device.  This left the Dell utilities the restore and the windows partitions.  I then booted 10.04 off my Live CD and entered without changes.

I used the disk utility to examine things and saw my windows partition was still intact. i was able to mount it in ubuntu and view the files.  I then elected to install Ubuntu 10.04.  I selected the "install side by side and choose between each at startup." It's currently at 83% and rising.

---

### Post by balaknair on 2010-07-10
Installing Ubuntu should help if it still recognizes your Windows install. It'll create a new MBR(Master Boot Record) and you should be able to boot from it.

If Ubuntu doesn't detect your Windows partition, you can still use testdisk to repair your partition tables and restore the MBR.

Reply here if you still have issues after your Ubuntu install, and I'll post instructions on how to analyse and restore the Windows partitions with testdisk.

All the best.

---

