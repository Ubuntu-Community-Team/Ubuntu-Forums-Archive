---
title: "120 gig SATA + 200 gig IDE ....?"
date: 2006-01-14
forum: General Help
---

### Post by msg on 2006-01-14
The computer came with a 120 gig SATA harddrive, decent sized, so I didnt wanna toss it, however it wasnt big enough (when my tv tuner arrives im installing mythTV and apache). My friend said installing an IDE harddrive alongside the SATA would be fine. After playing around I was able to run the ubuntu installation CD and partition the new disk with an ext3 FS, but when I boot up from my old SATA it wouldn't recognize the new one. I went to system>administration>disks (disks-admin) but it still didnt recognize it. Any suggestions?

---

### Post by mo_x on 2006-01-14
Run the follwing command from a terminal window and post the output.
```
sudo fdisk -l
```

---

### Post by msg on 2006-01-14
msg@ubuntubox:~$ sudo fdisk -l
Password:

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14401   115676001   83  Linux
/dev/sda2           14402       14589     1510110    5  Extended
/dev/sda5           14402       14589     1510078+  82  Linux swap / Solaris
msg@ubuntubox:~$

---

### Post by BathroomNinja on 2006-01-14
This sounds really dumb, but did you turn it on in the BIOS?
I'm running an IDE hard drive alongside a SATA and everything works great.
It shows my IDE drive as /dev/hda and my SATA as /dev/sda

So.. check your BIOS and make sure that it sees the new drive.

---

### Post by msg on 2006-01-15
I checked the BIOS, the only two options I have are OFF and AUTO for the harddrives. With auto on, it says "Unknown Device:. Also, what does 'IDE UDMA" mean and should i have it on or off?

---

### Post by kosmic on 2006-01-15
IDE UDMA should be on. please recheck that the cables and power supplie of the disk is well conected.

---

### Post by msg on 2006-01-15
Yeah i checked the cables, and it recognizes the disk when i have the SATA unplugged, but it just doesnt work when they are both plugged in. I turned IDE UDMA on. Maybe I have to set a jumper so it knows its the master drive, how do I set the jumpers on a SATA drive? there are four inline pins and I have no idea where to put it.

---

