---
title: "Ubuntu and NTFS"
date: 2009-06-12
forum: General Help
---

### Post by twjolson on 2009-06-12
I have three partitions.  First is ext3 with Ubuntu, and the second is a NTFS partition for Windows, and the third is NTFS where i keep data for easy backup.  I mainly access the data drive from Ubuntu, and ever since I installed ubuntu I've been getting alot of errors on that disk.  The Terminal will list a file as there, but if I try to delete it, it will say it isn't.  I'll make an ISO out of a CD, use it, and when I come back to use it later, it will read as 0 bytes in size.  Just wierd, wierd stuff.  I would think that the disk is going south, but I ran several checks on it and it checked out everytime.

My question is, could it be related to linux's implementation of NTFS?  Is it not as reliable as I thought? Or is there something else going on here?

Any utilities or tests you can think of to run that will help nail this problem down?

---

### Post by Bucky Ball on 2009-06-12
Open System->Administration->Synaptics Package Manager, do a search for 'ntfs-3g.' Install it. You will find it under the System->Admin drop down from memory (sorry, not on that machine right now). :)

Run that and it will put your drives into your fstab file. Give it a go once you've done all that.

Also, in a terminal, could you type:

sudo nautilus

... navigate to the file you want to delete and try to delete it. Can you?

---

### Post by Wayne_V on 2009-06-12
see "apt-cache show ntfsprogs".  maybe something there can help.

Are you getting errors in dmesg?  smartctl report the disk as OK?

---

### Post by colau on 2009-06-12
> **twjolson said:**
> I have three partitions.  First is ext3 with Ubuntu, and the second is a NTFS partition for Windows, and the third is NTFS where i keep data for easy backup.  I mainly access the data drive from Ubuntu, and ever since I installed ubuntu I've been getting alot of errors on that disk.  The Terminal will list a file as there, but if I try to delete it, it will say it isn't.  I'll make an ISO out of a CD, use it, and when I come back to use it later, it will read as 0 bytes in size.  Just wierd, wierd stuff.  I would think that the disk is going south, but I ran several checks on it and it checked out everytime.

My question is, could it be related to linux's implementation of NTFS?  Is it not as reliable as I thought? Or is there something else going on here?

Any utilities or tests you can think of to run that will help nail this problem down?
ntfs-3g is a nice utility for ntfs partition.
```

sudo aptitude install ntfs-3g

```
To manually mount ntfs drive
```

ntfs-3g /dev/sdaX /media/drive

```
Where X is the value of the partition number.

---

### Post by twjolson on 2009-06-14
ntfs-3g is installed already, I have the ntfsprogs, but don't know very much about them.  I did use the quick fix program, but that checked out ok.  The drive is mounted correctly.

The errors aren't coming from dmesg.  Like I said, I will browse the drive, either gui or command line, it will say something is there, say testfile.txt, and if I try to delete it, it tells me the file does not exist.  Furthermore, I installed a virtual machine via VirtualBox of Windows 7, all went well.  I exited out of VirtualBox, later when I came back in, the Windows 7 VM was gone.  Weird, so I looked at the spot on the disk where it should be, nothing was there.  Absolutely nothing.  No .vdi, no logs, nothing.

Like I said, it's weird, weird stuff, and I don't know what it causing it.  It's different programs, different files, different everything; the only commonality is Ubuntu and the NTFS drive.

I don't know, the only reason I need that drive as NTFS is so that I can read it in my native Windows install, and an XP vm I use as well.   Maybe I'll just convert it to Ext3 and then I can access it from the VM as a shared folder, regardless of the filesystem.

---

### Post by higet7 on 2009-06-14
> **twjolson said:**
> ntfs-3g is installed already, I have the ntfsprogs, but don't know very much about them.  I did use the quick fix program, but that checked out ok.  The drive is mounted correctly.

The errors aren't coming from dmesg.  Like I said, I will browse the drive, either gui or command line, it will say something is there, say testfile.txt, and if I try to delete it, it tells me the file does not exist.  Furthermore, I installed a virtual machine via VirtualBox of Windows 7, all went well.  I exited out of VirtualBox, later when I came back in, the Windows 7 VM was gone.  Weird, so I looked at the spot on the disk where it should be, nothing was there.  Absolutely nothing.  No .vdi, no logs, nothing.

Like I said, it's weird, weird stuff, and I don't know what it causing it.  It's different programs, different files, different everything; the only commonality is Ubuntu and the NTFS drive.

ntfs is for win, ext is for lin. while using (mounted partition) ntfs it is can be that processor will be overload so make a ext3 for a backup.

by the way. version of ubuntu? manual or automount?

may be that are crafty designs of balmer and it`s win7 ;)

---

