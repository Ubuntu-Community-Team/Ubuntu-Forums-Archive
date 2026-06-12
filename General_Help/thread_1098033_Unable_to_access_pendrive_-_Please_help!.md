---
title: "Unable to access pendrive - Please help!"
date: 2009-03-16
forum: General Help
---

### Post by Pipps on 2009-03-16
I used to be able to access my USB pendrive by opening a terminal and typing 'fdisk -l'. I am no longer able to do this and I do not understand why. Please help!

Earlier this evening I used the Ubuntu 8.10 live USB disc creator, whilst in CD-ROM live-mode, to attempt to make a live disc out of this USB pendrive. The process failed part-way through, so I restarted my machine and rebooted my system into my normal Ubuntu installation.

The pendrive has not been removed from the USB port on my machine. But now, when I open a terminal and type 'fdisk -l', the output it as follows:

```
Cannot open /dev/sda
Cannot open /dev/sdb
```

Now this is confusing, particularly because my pendrive has always been stated as /dev/sdc1, when inserted in that USB port, and it has not been removed since. Also, I have no other drives, other than my local single-partition hard disk, connected at this time. 

I now cannot see the pendrive in the terminal, in order to format it using the 'mkfs.ext3' command.

How should I format this pendrive and return it to its normal state? Thank you.

---

### Post by ajgreeny on 2009-03-16
Have a look with gparted.  That may well find it even if the partition has been corrupted in some way and show it as unallocated space which you can then format to whatever you want.  usually pen drives are either fat32 or even fat16.

---

### Post by Reeman on 2009-03-16
try a live cd and if you can reformat the pen drive to fat32 if it has been overwritten and the fs is corrupted there might be a chance to have the usb device show up with a live cd...but your usb automount on your install now shuts the thing out. 

Try it on another computer with windows you should be able to reformat it there even if it is not seen as a fat fs. If the partition sector of the thumb has been overwritten then the manufacture usually has software to detect it and re write the table but it will only work with windows unfortunately. I know this I have had to do the same thing with dane-electric 2gig.

---

### Post by Pipps on 2009-03-17
I loaded Gparted and formatted the drive that way, creating a new partition table in the process. My pendrive can now be accessed in the terminal again!

Thank you for your help!

---

