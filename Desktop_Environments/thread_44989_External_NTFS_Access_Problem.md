---
title: "External NTFS Access Problem"
date: 2005-06-28
forum: Desktop Environments
---

### Post by Ak37 on 2005-06-28
I got a problem when using/accessing my NTFS hard drive. This hard drive is an external drive, connected over USB. It mounts automatically, nothing wrong with that. But the problem is it can lock up the application that tries to access it.

It works at the first time after mounting. But then after the second or third access it freezes up. Sometimes accessing the drive from the Places Menu locks up Nautilus entirely. If this happens I can't even do an ls to the drive using the terminal.

I don't know why this happens, I've googled everywhere and no one seems to have the same problem with me. I've tried the Hoary Live CD and it reads the NTFS drive like a charm, no glitch at all.

One significant thing that I've done with my installation is using XFS for my root partition, could this be the source of the problem?

Thank You

---

### Post by jasmuz on 2005-06-28
[QUOTE=Ak37]I got a problem when using/accessing my NTFS hard drive. This hard drive is an external drive, connected over USB. It mounts automatically, nothing wrong with that. But the problem is it can lock up the application that tries to access it.

It works at the first time after mounting. But then after the second or third access it freezes up. Sometimes accessing the drive from the Places Menu locks up Nautilus entirely. If this happens I can't even do an ls to the drive using the terminal.

I don't know why this happens, I've googled everywhere and no one seems to have the same problem with me. I've tried the Hoary Live CD and it reads the NTFS drive like a charm, no glitch at all.

One significant thing that I've done with my installation is using XFS for my root partition, could this be the source of the problem?

Thank You[/QUOTE]
 Hello there.
Not at all...i have also access to a NTFS where i keep my mp3 files, and i get random lockups...i kill the application and it goes zombie on me.

The problem itself is the reading of the NTFS, havent found a way to fix this yet.

One other thing, you shouldnt of installed XFS to your root partition unless you are handeling  HUGE files. I would of recommended ReiserFS instead.

---

### Post by Ak37 on 2005-06-28
Thank you for the reply. I think of reinstalling my Ubuntu Installation with something other than XFS. I'm sure Ubuntu has the capability of reading my NTFS drive without crashing, the Live CD works fine.

What Filesystem should I use best? I'm using a Laptop here. I heard that ReiserFS could take up more CPU than other FS?

---

### Post by Ak37 on 2005-07-04
Problem solved (I think) 

Googled some more and it seems that someone pointed out that there is some bug which causes the data rate to be too-fast for the disk causing a halt. I don't know the technical explenation, but I plugged in my USB Hub between my laptop and external hard drive. It's a USB 1.0 hub which means everything now runs at a significantly slower rate.

The drive runs for several hours without a crash. It feels a lot slower, but running slow is better than not running.

The (partially) problem is addressed but I hope the next release of Ubuntu could make it run better out of the box. I know it's possible because Hoary Live CD doesn't have any problem with it.

---

### Post by GTvulse on 2005-07-04
It is not Ubuntu's fault, but a problem with the USB Mass Storage driver in the kernel. Your first bet would be to try building a kernel from the latest stable version, Linux 2.6.12.2 at the time of writing, and see if the bug-fixes in that one help you. (I solved several problems with video card acceleration by rolling out my own kernel off the latest stable sources). 

You download the sources from [Kernel.org](http://www.kernel.org/) and follow the instructions given in the [Kernel compilation HOWTO](http://ubuntuforums.org/showthread.php?t=43065)

---

### Post by pepevilluela on 2007-05-14
I'm suffering same problem in feisty:

I could mount my IOMEGA external ntfs hard disk in edgy and copy large files like videos. Since y updated to feisty I can mount with ntfs-3g, see what's inside, but when i copy my disk looks as it were frost, tells me that it will take 129 hours, and nothing moves in progress bar. Anybody can solve it?

---

