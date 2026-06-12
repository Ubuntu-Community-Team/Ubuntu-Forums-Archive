---
title: "External HD is only read-only"
date: 2006-03-04
forum: Desktop Environments
---

### Post by tidy_boy on 2006-03-04
hey guys I have a 250gig hard disk in a caddy connected via usb. the problem is  i cant actually save anything on it.

How do I make it so I can save stuff on it?

---

### Post by bluevoodoo1 on 2006-03-04
[QUOTE=tidy_boy]hey guys I have a 250gig hard disk in a caddy connected via usb. the problem is  i cant actually save anything on it.

How do I make it so I can save stuff on it?[/QUOTE]

What format is it? Ubuntu can't write to NTFS, only read.

---

### Post by tidy_boy on 2006-03-04
Wel I have not converted it to anything so its still ntfs

---

### Post by akiro.yamamoto on 2006-03-04
What type of file system do you have on the harddrive, Fat32, NTFS, EXT3 or other?
Did you set-up your entries for the HD in your fstab?
Some more details please!

---

### Post by tidy_boy on 2006-03-04
Sorry I am very new to all this. I have not set anything up with my external hard disk

---

### Post by akiro.yamamoto on 2006-03-04
Well create an entry in your fstab for it.
Something like:
/dev/sda1 /media/usb-hd ntfs user,ro,umask=0222 0 0
May help

Edit:
Of course modify as needed ;)
The /dev may be something else, as well as the mount point you designate.

---

### Post by tidy_boy on 2006-03-04
sorry how do i get to my fstab like I said I am very new to all this :D

Thanks

---

### Post by taurus on 2006-03-04
If you want to be able to write to that hd in Ubuntu and Windows, then better format it as fat32 (vfat) because Linux can't write to NTFS, yet!!!

---

### Post by tidy_boy on 2006-03-04
Taurus hwo do i format it to fat32 please :D

---

### Post by towsonu2003 on 2006-03-04
you can use gparted (search for it in synaptic package manager system>administration>synaptic>reload>search>gparted) to repartition and / or reformat the drive (I'd say to fat32). be **veryveryvery** careful not to format some other drive by mistake. also formatting will erase everything in that drive. 

once you install gparted tru synaptic, it goes to applications>system tools>gparted. plug in drive, launch gparted (should ask for your password), and play around with the drive in gparted without saving for some time, until you are sure you are not formatting something else and the parttitioning is correct. it should not save your changes if you do NOT hit apply / save button (don't remember which one is there).

---

### Post by incubus on 2006-03-04
tidy,

Wait, wait. You said you can read files but not write, correct? Before anything let's see what is the current file system there. Type:
$ mount

Find which line corresponds to your external hard drive and check the type. If you decide to erase everything and create a different file system, you can follow townsonu's post, google, or search the forum for a how-to. 

But remember that Fat32 is limited to 32Gb, which may be the reason why things are not working now (your HDD is 250Gb).

Check this thread:
[http://www.ubuntuforums.org/showthread.php?t=139423&highlight=fat32]("http://www.ubuntuforums.org/showthread.php?t=139423&highlight=fat32")

If you use Linux as your primary OS and windows sometimes, I would format the partition as Ext2 and install that windows driver I mention. But that's my personal opinion.

incubus

---

### Post by helfrez on 2006-03-11
Not entirely correct, Linux can write to NTFS and has had the ability for quite some time, read-only mode is the most stable at the moment. However recent kernels like 2.6.15 have considered ntfs write stable, most distributions like Ubuntu just dont compile write support into the kernel by default...

---

