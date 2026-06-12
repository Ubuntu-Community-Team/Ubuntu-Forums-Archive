---
title: "How To:  Ubuntu &amp; Windows seeing each other"
date: 2010-06-18
forum: Desktop Environments
---

### Post by u2rcrazy on 2010-06-18
I'm running a dual boot machine with Ubuntu 10.45 and Windows 7.  Ubuntu is able to see the windows partition, but Windows can't see Ubuntu.  Also I have a second Ubuntu partition that I believe I made the Home folder, but I'm not sure if this is the case.  How can I enable my Ubuntu partitions to be seen by Windows?  To help assist you, I have provided a screen shot of GParted which shows how the drive is decided up.

[ATTACH]160806[/ATTACH]

Thanks for your time!!

Bob:guitar:

---

### Post by JimSBjd on 2010-06-18
Hey, I'm pretty new at this, but my general understanding is this:

Ubuntu (and most linux distros also) use a filesystem that is either ext3 or ext4.  10.04 for example uses ext4 as a default filesystem.  They also have support built in to be able to read/write to an NTFS or FAT/FAT32 partition.

Windows 7/Vista/XP/2000/NT use a filesystem called NTFS.  They can also support FAT/FAT32.  They DO NOT have the inherent ability to read or write to a linux filesystem such as ext4.

So, in a dual boot situation, where one partition has Ubuntu, and another partition Windows 7, Ubuntu can mount the Windows 7 partition, but Windows 7 cannot mount the ext4 partition.

About the only way for Windows 7 to see files on an Ubuntu machine is if they are separate computers, and you use Samba to set up a workgroup - then Windows 7 can see files placed in a share folder on the Ubuntu machine.

Hope that helps.

---

