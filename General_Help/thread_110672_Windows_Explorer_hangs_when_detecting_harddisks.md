---
title: "Windows Explorer hangs when detecting harddisks"
date: 2005-12-31
forum: General Help
---

### Post by witvloerkleed on 2005-12-31
Hi,

I just installed Ubuntu on my Win2k system. I have 2 harddisks with several partitions on each, windows is on the master disk and the slave has several NTFS/PAL partitions and a Ext3 with Ubuntu and a SWAP partition.

First when I restarted after running windows GRUB gave error 17. I knew my motherboard had a problem recognising my 80 GB hd so I updated my BIOS and the problem was solved. 

One problem remains: when I start **Win2k it hangs for about 5 min on the blue screen** while loading, this didn't happen before. Then in windows everything seems fine until I open Explorer. **When I click a disk it needs 5 minutes to "recognise" it**. Also when I use for example winamp or paint and I want to open a Dir the program freezes. 

This is very annoying. Can anyone help me? Thanks in advance.

---

### Post by Luffield on 2005-12-31
I had the same problem after I installed Ubuntu on my Win2000 machine. I have a 30gb drive on which Win was installed, and a 3gb drive that I used for Ubuntu. The small disk used to be D: on windows, and it was FAT32. After I installed Ubuntu windows couldn't read the disk because now it was an EXT3 disk, so it gave the symptoms you describe.

The solution I used was to create a new hardware profile in Windows, in which the smaller disk is disabled. I'm pretty sure that I followed instructions I found in this forum, but I'm afraid I can't find them now. I'll try again later if you don't get better answers by then.

I am, however, a bit worried that this solution may not be the right one for your system, because I had only one partition on that disk and I understand that you have more than one.

---

### Post by OrangeGoblin on 2005-12-31
I had the same problem, just went to device manager and disabled the HD and it was ok.

---

