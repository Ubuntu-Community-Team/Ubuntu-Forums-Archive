---
title: "USB disk and a digital camera mounts to the same place, how can I change it?"
date: 2006-01-14
forum: Desktop Environments
---

### Post by sup on 2006-01-14
Hello, I have got an USB external harddrive and a digital camera. They both identifies themselves as /dev/sda1 and both have FAT32 file system. I have got the followig line in my /etc/fstab:
```
/dev/sda1	/media/share		vfat		defaults	0	0
``` so it is clear they both mount themselves to /dev/sda1, which is something I do not want. Is there any way to make them not to behave such way? I have no idea how to make them work like that.

---

### Post by awi on 2006-01-25
Have you tried without the /etc/fstab entries?   I solved that problem letting default ubuntu (at least breezy, with hotplug) automount the devices. My external USB HD has the volume name "AWI", and my  pendrive has another, "ACME", and they get mounted on /media/AWI and /media/ACME respectively and they show up in nautilus, automatically.

---

### Post by Sutekh on 2006-01-25
[QUOTE=sup]Hello, I have got an USB external harddrive and a digital camera. They both identifies themselves as /dev/sda1 and both have FAT32 file system. I have got the followig line in my /etc/fstab:
```
/dev/sda1	/media/share		vfat		defaults	0	0
``` so it is clear they both mount themselves to /dev/sda1, which is something I do not want. Is there any way to make them not to behave such way? I have no idea how to make them work like that.[/QUOTE]
I sat for a while thinking; 'how can both devices identify themselves as /dev/sda1?'

Do you only connect one device at a time?  Either the Ext. Drive or the Dig. Camera separately? 

If both are connected at the same time, using different USB ports, they must be considered different devices.

---

### Post by sup on 2006-01-27
> I sat for a while thinking; 'how can both devices identify themselves as /dev/sda1?'
Do you only connect one device at a time? Either the Ext. Drive or the Dig. Camera separately? 
If both are connected at the same time, using different USB ports, they must be considered different devices.	
1 Day Ago 12:27 AM
I only connect one device at a time. Of course they identify differently when connected both at the same time. Yet then again,  I would like them to mount on different directories when connected on at a time (for creating bookmarks in Krusader for example).
> Have you tried without the /etc/fstab entries? I solved that problem letting default ubuntu (at least breezy, with hotplug) automount the devices. My external USB HD has the volume name "AWI", and my pendrive has another, "ACME", and they get mounted on /media/AWI and /media/ACME respectively and they show up in nautilus, automatically.
Hump, I could give that a try, but I somehow dislike names Ubuntu chooses for my harddisk, however I guess can get used to it.

(But then again it is just a workaround, I would like some straightforward solution
liek somthing telling the computer to mark the harddisk as sda and the camera as sdb)

---

### Post by sup on 2006-05-08
I found that solution are volume labels (or names or whatever you call it). Programs like mke2fs (-l option i think) or msdosfs (-n option I think) can set it and ubuntu then mounts the volume in /media/volume_label - so /etc/fstab can be modified so that //network/volume will mount there as well. Nice and clean, just as I wanted, nice.

Humph, I see Awi suggested just that, too bad I did not understand her at that time.

---

