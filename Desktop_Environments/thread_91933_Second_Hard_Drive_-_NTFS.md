---
title: "Second Hard Drive - NTFS?"
date: 2005-11-18
forum: Desktop Environments
---

### Post by Zodiac on 2005-11-18
I have two harddrives in my windows comp... one is where windows resides the other is strictly for mp3z. 

Is it possible for the second drive to be formatted in NTFS even if windows is not on it? How can I tell?

How can I change it so that if I decided to install Ubuntu I could read/write to it?

Thanks!

---

### Post by earobinson on 2005-11-18
Sure just use partition magic (or any other partition program and make it an ntfs drive) reading and writing in ntfs is very very unstable right now if not imposiable so It would need to be in fat32 or something else that both ubuntu and windows can read and write to.

---

### Post by aysiu on 2005-11-18
Ubuntu can read/write FAT32, not NTFS.
If you're in Windows, go to the Control Panel and find the administrative options. There should be something in there like Disk Information that'll tell you if it's NTFS already.

---

### Post by earobinson on 2005-11-18
[QUOTE=aysiu]Ubuntu can read/write FAT32, not NTFS.
If you're in Windows, go to the Control Panel and find the administrative options. There should be something in there like Disk Information that'll tell you if it's NTFS already.[/QUOTE]
I was under the impresion that it could be done just it is very unstable
> NTFS Writing on Linux is very sketchy right now. I wouldn't try it Source: [http://www.ubuntuforums.org/showthread.php?t=88054&highlight=ntfs+network](http://www.ubuntuforums.org/showthread.php?t=88054&highlight=ntfs+network)

Is this not correct aysiu?

---

### Post by suRoot on 2005-11-18
I don't understand whether you're currently looking at the drive under Windows, but assuming so just right-click the drive & do properties.  You'll see what kind of filesystem it's using on that main tab.

Linux can read NTFS just fine & if you installed Ubuntu it would see the drive & mount it for you... but if you value your data I wouldn't recommend writing to it that often as NTFS write is still considered experimental (and it probably always will be too, since It's a proprietary MS filesystem).

Don't know how large the drive is or if you have media capable of backing it up - DVD+/- R , CD-R , etc but that's probably the easiest thing to do - in fact, so far as I know it's the only thing you can do.  You can convert FAT32 to NTFS but not back.  Maybe there's a utility out there that will do it, but I'm not familiar with it.  Just back up your data & wipe the drive clean.  If you need to share the drive with Windows, dual-booting or whatever, format the drive as FAT32.  Only downside to that is that you're stuck with a 32GB partition limit.  Again, may or may not be a problem depending on how large your drive is & whether it annoys you having umpteen partitions on your drive.  If you're going to just run Linux, let the installer partition it for you with Reiser4 or XFS (that would be my suggestion), but any of the Linux filesystems would be fine.

---

### Post by Zodiac on 2005-11-18
Well the drive is really a second hard drive.... it is a completely separate dedicated drive... I am crossing my fingers that it isn't in NTFS but I have a sneaking suspicion it is.

So if I back up all the data.... how do I format the drive into FAT32?

Is there a free utility I can use?

---

### Post by suRoot on 2005-11-18
Assuming you're doing it in Windows, just right-click My Computer -> Manage -> Disk Management -> Right-click the disk & delete the partion if necessary.  Create new partitions depending on how large your disk is & you'll be prompted to format them.

If you're using Linux you can do it with gparted.

---

### Post by aysiu on 2005-11-18
[QUOTE=suRoot]
If you're using Linux you can do it with gparted.[/QUOTE] Or even using the partitioning tool that's in the Ubuntu installer.

---

### Post by Zodiac on 2005-11-28
Will partitioning the drive destroy data that is on it?

Will I be able to copy the data on the drive over to main if it is in NTFS?

---

