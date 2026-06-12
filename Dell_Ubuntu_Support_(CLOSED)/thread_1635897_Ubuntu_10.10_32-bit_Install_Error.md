---
title: "Ubuntu 10.10 32-bit Install Error"
date: 2010-12-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ntonline on 2010-12-02
Hey all,

I am running a machine that came with Windows XP preinstalled.  I've  been having trouble with Windows performing very, very slowly; plus the  audio on my machine sounds garbled.  Since I have been having so many  problems, I decided to partition my hard drive to install Ubuntu to give  it a try.  

I split my C: drive into two separate partitions.  There were three  originally partitions, so now there are a total of 4 partitions.  My  hard drive is an 80GB drive and allocated 35GB to my C: drive (for XP)  and 35GB to my E: drive (for Ubuntu).  

I downloaded Ubuntu 10.10 from Ubuntu.com and burned the image onto  disk.  I inserted the disk into my computer and restarted the machine.   The installation did not occur as expected when the machine started up.   I ended up having to install some software so the computer would  recognize the disk on startup.  After installing this software, I  restarted my machine again, and this time the installation of Ubuntu  began.  During the install, at around 60 percent, the installation  failed.  A message appeared stating something to the effect that the  installation directories were not found.  At this point I attempted to  install Ubuntu a second time, but the second install attempt failed at  the same point and with the same message.  

Frustrated, I rebooted my computer and was greeted by the following error:

```
error: unknown filesystem.
grub rescue>
```Now my computer would not even boot Windows XP.  I  am new to linux and  spent many hours trying to research this error and  have not found anything that resolved this particular issue.

Whenever I enter a command at the grub rescue prompt I am told the  command is an Unknown command.  The only command that is recognized is  the "ls" command, which yeilds the following:

```
error: unknown file system.
grub rescue> ls
(hd0) (hd0, msdos6) (hd0, msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (fd0)
grub rescue>
```How do I fix this problem?  I'm trying to set up a  dual boot option on my machine so I can access XP or Ubuntu.

Hardware:
Dell Dimension 3000
80GB hard drive
Windows XP
Intel Celeron processor

I can't get the exact specs because I don't know how to look them up  from the command prompt and I can't get the machine to boot XP right  now.

---

### Post by Joe of loath on 2010-12-02
Have you tried re-burning the CD?

---

### Post by Thelinuxgeek on 2010-12-02
That happens when there's data missing from the disc. I had the same problem once. You've screwed your machine, I'm sorry to say. You'll have to re-burn the Ubuntu disc at a lower burning speed to ensure everything is written correctly, and if you want to, re-install Windows XP. Sorry! I feel your pain...

---

### Post by Joe of loath on 2010-12-02
I wouldn't say it/s screwed at all, it just needs a bootloader so you can get back in to Windows again.

---

### Post by ntonline on 2010-12-02
> **Joe of loath said:**
> it just needs a bootloader so you can get back in to Windows again.

I'm curious what is a bootloader is and how can I use a bootloader to get back into windows?

---

### Post by Joe of loath on 2010-12-02
A bootloader is what starts the loading of the OS. Windows has its own, which was overwritten with one of the bootloaders for Linux, GRUB, when you tried to install Ubuntu. However, as the install wasn't completed (probably due to a bad CD), the GRUB install was corrupted and wouldn't let you boot into Windows.

The easiest easiest way to fix it all is to burn another copy of Ubuntu and to try install again. That way GRUB will be installed successfully, and you'll be able to dual boot.

---

### Post by ntonline on 2010-12-02
> **Joe of loath said:**
> The easiest easiest way to fix it all is to burn another copy of Ubuntu and to try install again. That way GRUB will be installed successfully, and you'll be able to dual boot.

I downloaded Ubuntu 10.10 again and burned a new disk.  However, when I insert the disk into the machine and attempt the install, the install does not move passed the Ubuntu image with the lines scrolling across the bottom.

Is there anyway to force the installation of Ubuntu at this point?

---

### Post by oldfred on 2010-12-02
Ubuntu will only install to NTFS if you are installing wubi. The normal dual boot requires Linux file types ext3 or ext4 normally. If you did not specify a / (root) and swap partitions then it does not install. Do not know why it then installed grub over your windows boot loader in the MBR.

You need to delete your E: partition and create Linux partitions.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM.

---

