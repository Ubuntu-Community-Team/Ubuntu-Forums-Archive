---
title: "How do I prevent Windows from killing Ubuntu!"
date: 2008-12-15
forum: General Help
---

### Post by MR.UNOWEN on 2008-12-15
So for those who have both XP and Ubuntu running, you know Windows is unfriendly when installing and will remove Ubuntu off of the boot record.

So I'm getting a laptop and unlike a desktop where you can have an OS on separate hard drives (allowing me to choose which on by leaving only one on), now I have to have them share one hard drive.

How can I have both installed, without me worrying about loosing Ubuntu every time I need to re-install Windows? 

If I want the boot record to stay on Ubuntu, how do I install both to be in that way?

Is there a way through Ubuntu that I can back up my Windows partition, such that I can replace the partition with the backup instead of me reinstalling everything?

Is there a way I can lock windows register such that I don't have to worry about needing to reinstall it?

---

### Post by 2hot6ft2 on 2008-12-15
It's not that hard all you would have to do is reinstall the grub bootloader from the livecd after re-installing windows. Naturally there are always other options and here is one.

backup partitions into a compressed image file
Partition Image is a partition imaging utility. It has support for the
following file systems:
 * Ext2/3, the Linux standard
 * ReiserFS, a journalised and powerful file system
 * FAT16/32, DOS and Windows file systems
 * HPFS, IBM OS/2 file system
 * JFS, journalised file system, from IBM, used on AIX
 * XFS, another journalised and efficient file system, from SGI, used on Irix
 * UFS (beta), Unix file system
 * HFS (beta), MacOS File system
 * NTFS (experimental), Windows NT, 2000 and XP
Only used blocks are copied and stored into an image file.
The image file can be compressed in the GZIP/BZIP2 formats to save disk space, and split into multiple files to be copied onto removable media (ZIP for example), burned on a CD-R, etc.

This makes it possible to save a full Linux/Windows system with a single
operation. In case of a problem (virus, crash, error, etc.), you just have
to restore, and after several minutes, your entire system is restored
(boot, files, etc.), and fully working.

This is very useful when installing the same software on many machines: just install one of them, create an image, and restore the image on all other
machines.

---

### Post by 2hot6ft2 on 2008-12-15
Another one
> Clonezilla, fastest ever cloning i have ever done is using CLONEZILLA(indeed it is top notch app).

i have cloned several HDD and networked machines with it, locally and on network with no problem what so ever. Great app for one off complete system state clone/backup

Last week I cloned my laptop's HDD 120GB locally within 35 mins.

[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

Haven't used these myself they are favorite apps from the thread of the same name "Favorite apps you use that others may not know of" or something like that.

---

### Post by la3875 on 2008-12-15
Don't panic is the first rule. Its really quite easy to manipulate. Make sure windows is instaled first, then install Ubuntu.

See also:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Enjoy!

---

### Post by Seq on 2008-12-15
> **MR.UNOWEN said:**
> So for those who have both XP and Ubuntu running, you know Windows is unfriendly when installing and will remove Ubuntu off of the boot record.

Yes, when installing Windows. Most folks simply install Windows first.

> **MR.UNOWEN said:**
> So I'm getting a laptop and unlike a desktop where you can have an OS on separate hard drives (allowing me to choose which on by leaving only one on), now I have to have them share one hard drive.

How can I have both installed, without me worrying about loosing Ubuntu every time I need to re-install Windows? 

Just partition your drive how you want it. Say you have a 80GB drive and you want 20GB windows with the rest for Linux:

Start the windows install, create a partition sized 20GB, then install. Then install Ubuntu, creating partitions in the remaining space. Ubuntu's installer will install Grub to the MBR, and will add Windows to the boot menu.

> **MR.UNOWEN said:**
> Is there a way through Ubuntu that I can back up my Windows partition, such that I can replace the partition with the backup instead of me reinstalling everything?

I've had success with my workstation at work using partimage, though I had used a live cd (sysrescuecd) as Ubuntu's (Hardy at the time) crashed on NTFS for some reason. Also, be sure to not have your windows partition mounted when doing this.

> **MR.UNOWEN said:**
> Is there a way I can lock windows register such that I don't have to worry about needing to reinstall it?

Don't boot it, and only mount ro. :)

---

### Post by 2hot6ft2 on 2008-12-15
Here's one I have used in windows. I just took another drive the same size as the one I was using and cloned it. If something went wrong I would just swap drives and keep going. Then I would clone that one back to the other drive. Worked great [http://www.xxclone.com/](http://www.xxclone.com/)

---

### Post by MR.UNOWEN on 2008-12-15
How do I ensure that Ubuntu has the boot record? I don't want to kill Ubuntu if I erase XP.

---

### Post by TeXtonyx on 2008-12-15
> **MR.UNOWEN said:**
> How do I ensure that Ubuntu has the boot record? I don't want to kill Ubuntu if I erase XP.

XP is installed by default to the MBR. Ubuntu is installed by default
to the MBR. So whichever OS you install last controls the MBR,
and so with XP uses boot.ini and with Ubuntu uses grub/menu.lst.

With either OS you don't have to make a new installation of the OS.
You can reinstall grub, or you can fixmbr with XP, to reclaim the
MBR and assign either OS to the MBR. Grub is more flexible than the
XP bootloader and grub can be installed to the /boot partition.
Then with a boot disk you can always boot into Ubuntu independently
of XP. You can add Ubuntu to the boot.ini with free Bootpart
and boot both XP and Ubuntu from XP and maintain a safety net
to boot Ubuntu by grub boot disk if XP fails. If that sounds
complicated just remember you can reinstall grub to the MBR
without reinstalling all of Ubuntu. Ubuntu is in another partition
than XP unless you have used something called Wubi. If you want to
delete the XP partition from the drive, only delete NTFS. The worst
that can happen is that you have to reinstall grub from the live cd.
Don't guess at what is the NTFS XP partition, you could make an error.

---

