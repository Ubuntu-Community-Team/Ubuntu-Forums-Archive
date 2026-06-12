---
title: "How to resize my partitions?"
date: 2006-08-22
forum: Desktop Environments
---

### Post by fatsheep on 2006-08-22
I have a 40 GB hard drive with 2 partitions - Windows XP and Ubuntu.  Currently the XP partition takes up waaaaaaay too much space, I need more of it on Ubuntu so I was going to downsize my XP partition and enlarge my Ubuntu partition.  I thought this was going to be a simple task, apparently not.

I have tried the Ubuntu Live CD.  The partition editor on it freezes when you apply your requested changes (and yes I have tested this more then once).

I have tried using Gparted and Gnome Partition editor on Ubuntu, the options to downsize the XP partition are grayed out.  Same goes for the disk management partition editor on XP.

I have tried using the Partition Magic boot up CD.  I got an error.

I tried to use Disk Drake on PCLinuxOS installation CD but no matter what torrent or download I use, it's ALWAYS ALWAYS corrupted.  


**Any help would be greatly appreciated.** :)

---

### Post by Scythe!? on 2006-08-22
> **fatsheep said:**
> 

I tried to use Disk Drake on PCLinuxOS installation CD but no matter what torrent or download I use, it's ALWAYS ALWAYS corrupted.  


**Any help would be greatly appreciated.** :)
If it's always corrupted, I'd be worried about dodgy RAM to be honest. Run memtest86 on a few tests to see if anything shows up.

GParted didn't work on the Live CD for me either but the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") worked.

---

### Post by fatsheep on 2006-08-22
I tried the Gparted Live CD but got a fatal server error "no screens found" and it booted me to a limited shell. :confused: 

So, as you recommended I decided to run memtest.  I let it run for 27 minutes and received no errors. :-k

---

### Post by robenroute on 2006-08-22
Fatsheep,

You mentioned that the options for resizing are greyed out; could it be that these partitions you're trying to resize are still mounted? You can only resize them after you've unmounted (umount) them. Hope this helps.

Rob

---

### Post by fatsheep on 2006-08-22
> **robenroute said:**
> Fatsheep,

You mentioned that the options for resizing are greyed out; could it be that these pertitions your trying to resize are still mounted? You can only resize them after you've unmounted (umount) them. Hope this helps.

Rob

Didn't know that, thanks for the info. :D  How do I unmount my partitions?

---

### Post by atomkarinca on 2006-08-22
on gnome partition editor you can unmount the partition by right-clicking on it or you can use umount on the terminal. then you can resize the partitions.

---

### Post by fatsheep on 2006-08-25
> **atomkarinca said:**
> on gnome partition editor you can unmount the partition by right-clicking on it or you can use umount on the terminal. then you can resize the partitions.

When I try to do that it fails, just gives me an exclamation mark with an error = 

> Unable to read the contents of this file system.  
Because of this some operations may be unavailable.

Did you install the correct plugin for this filesystem?

---

### Post by masnevets on 2006-08-26
If you're using gparted from Ubuntu, you'll need to download ntfsprogs

sudo apt-get install ntfsprogs

But there might be a problem resizing a partition if it's on the same harddrive as your Ubuntu install. If that happens I recommend using the gparted liveCD as it works well. For your gparted liveCD problem, I don't remember what you need to pick for the graphics settings, but if you try different ones you should be able to get around the "no screens found" message.

---

