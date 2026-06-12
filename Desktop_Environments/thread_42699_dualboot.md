---
title: "dualboot"
date: 2005-06-19
forum: Desktop Environments
---

### Post by vreemde eend on 2005-06-19
I've got Ubuntu running on an old pc that's hardly used. But i really like (K)Ubuntu so I would like to have a dual boot (with WinXP) on a newer pc. I want Ubuntu and WinXP to share my documents (text, .psd, music, film, ...). I'm a newbie to these things and even don't know if this is possible. I'v got a 120Gb HD, don't play games, frequently use Photoshop and Illustrator (if this has got any relevance). My computer needs a format.

Any suggestions for the partions and how do I start/do this?

---

### Post by defkewl on 2005-06-19
First make a Linux partition and swap partition to install ur Ubuntu. You can do this with fdisk or visually with partition magic from windows.

---

### Post by Civil on 2005-06-20
I bought an Acer laptop with WinXP (Home) pre-installed.  The 30GB hard drive was already partitioned into two drives - C and D.

I deleted the D partition (using WinXP tools), then re-partitioned about 7 GB of space for a D drive in Windows.  I left the remaining space for Linux.  This will only work on newer systems where you don't have the LBA restriction in the BIOS.

Put in the Ubuntu CD and tell the partitioner to use the free space.  Go ahead and let Grub install on the Master Boot Record when prompted.

After that, I had a great dual-boot system.  For me, I use the WinXP "D" drive for "DATA".  That is where I save all my documents, music, etc.  And I mount that same drive using FSTAB in Linux as "osshare" so it is available on a Linux boot.  It really works great.

---

### Post by Embajador on 2005-06-20
If you need format it will be easy. Just run XP installation from CD and follow the steps until you arrive on where you want to install the OS (C by default). Just choose the amount of GB's you want to give to XP and leave the rest free. Proceed with XP installation. After you're finished boot Kubuntu install CD and follow instructions. Once you arrive to where to install options you'll find two options: where XP is, and free unasigned space. Just choose the second. The dual boot will be automatized with GRUB. It's all you need to do. Hope this info is helpful.

---

### Post by Embajador on 2005-06-20
Sorry, I forgot to tell you that you can access your Windows partition from Kubuntu. You just have to mount Windows device. Is very easy to configure and you can copy your Windows files onto Linux partition. But as far as I know the other way, accessing Linux files from Windows, can be done but in a very difficult way and only in read only mode.

---

### Post by arjaybe on 2005-06-20
[QUOTE=vreemde eend]I've got Ubuntu running on an old pc that's hardly used. But i really like (K)Ubuntu so I would like to have a dual boot (with WinXP) on a newer pc. I want Ubuntu and WinXP to share my documents (text, .psd, music, film, ...). I'm a newbie to these things and even don't know if this is possible. I'v got a 120Gb HD, don't play games, frequently use Photoshop and Illustrator (if this has got any relevance). My computer needs a format.

Any suggestions for the partions and how do I start/do this?[/QUOTE]

I agree with Embajador, with a couple of additions.  You said you wanted a data partition to share between OSes, so after installing Windows you should boot it and carve a partition (10, 20, 30GB?) out of the free space.  Format it FAT32 for now.  When NTFS is fully supported you can change it if you want.

When installing Ubuntu, don't use up all the remaining free space. (I'm assuming you have tens of gigabytes left)  Ubuntu runs comfortably with lots of room in 5GB, but there's nothing wrong with 10GB.  It's always good to have too much disk space.  The remaining free space will be there if you want to install another distribution (or two or three or four . . .)  Or if you need more data space.  Or to make a clone of your Windows install for when it eats itself.  Or . . .

Anyway, welcome to the world of free software.  Enjoy yourself.

---

### Post by vreemde eend on 2005-06-21
Thanks a lot for your help. It seems to easier then I thought. I'll try it next week (something came between it). Is it possible to 'automount' the partition that I want to share with Windows at Unbuntu startup?

again, thanks for your help

---

### Post by deBaas on 2005-06-21
[QUOTE=vreemde eend]Thanks a lot for your help. It seems to easier then I thought. I'll try it next week (something came between it). Is it possible to 'automount' the partition that I want to share with Windows at Unbuntu startup?

again, thanks for your help[/QUOTE]
automount is no problem at all. Take a look at ubuntuguide.org
Use 1 partition for windowsXP
Use 2 partitions for ubuntu (one is swap)
use 1 FAT32 partition Both WinXP and ubuntu can read and write to that partition.

---

### Post by vreemde eend on 2005-07-01
It's up and running, no problems at all (except I had to instal WinXP twice because of an serious error, nothing to do with Ubuntu). 

The only problem left is that I can't connect Internet with my Eicon Adsl USB modem. The modem is listed in the device manager, but doens't work. Anybody knows how to get it work? (I tried this: [http://ubuntuguide.org/#rp-pppoe](http://ubuntuguide.org/#rp-pppoe), did nothing at all.)

thanks,

vreemde eend

---

### Post by vreemde eend on 2005-07-02
As this is a different question, I posted it elsewhere: [http://ubuntuforums.org/showthread.php?t=45923](http://ubuntuforums.org/showthread.php?t=45923) . All help is welcome. 

thanks in advance,

vreemde eend

---

