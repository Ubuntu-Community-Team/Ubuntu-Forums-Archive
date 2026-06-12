---
title: "Use GRUB to Boot Ubuntu with Windows XP"
date: 2010-12-20
forum: Desktop Environments
---

### Post by dz3 on 2010-12-20
I'm wondering about the best way to manage a dual install of Ubuntu and Windows XP.

I had Ubuntu installed on my HDD, but I wanted Windows also, so I used a live CD to partition the drive, and opened some space for a Windows partition. I installed Windows in that space. Naturally, the install set up the computer to boot directly into Windows. I want to set up GRUB to load and allow me to choose my OS on boot.

I'd like to use Super GRUB Disk to install GRUB on the MBR of the disk to allow me to choose at boot.

Thanks in advance!

---

### Post by wojox on 2010-12-20
Just [Reinstall from a LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by wilee-nilee on 2010-12-20
You don't want a supergrub disc unless its the last resort.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

This will tell what is where and grub will just be put in the MBR=bootloader for a choice of Ubuntu or XP, most likely.

---

### Post by mr clark25 on 2010-12-20
if you just want to install grub, the link in my signature should do it all for you.

---

