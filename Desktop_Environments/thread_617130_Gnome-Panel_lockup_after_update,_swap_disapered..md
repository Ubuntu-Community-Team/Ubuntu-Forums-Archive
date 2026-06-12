---
title: "Gnome-Panel lockup after update, swap disapered."
date: 2007-11-19
forum: Desktop Environments
---

### Post by Tango_Down on 2007-11-19
Well, I updated from breezy to Gusty a few weeks ago, and now gnome-panel freezes, this struck me as odd. I checked top and it told me that it only freezes when I start running out of RAM. What about my swap? Well, I checked free to find out that I had a swap, it just was of size 0. This struck me as odd. Gparted tells me that my swap partition is there and still the 500 megs that I made it in the beginning. It seems that it is somehow corrupted however, and does not show up as linux swap format. Other people have had the same problem with Gnome-Panel after update, and found out that there swap partition was corrupted. Could there be something about the update process that corrupts the Swap Drive? I certainly can't think of such an occurrence. I will reformat the swap drive and see if Gnome-Panel stabilizes.

---

### Post by Tango_Down on 2007-11-19
Attempting to reformat swap drive while running from HD installation leads to segmentation fault and a core dump. Classy. For reasons I don't understand, none of my live CD's will work anymore. They get to "Probing devices" and proceed to freeze up. This is with Knoppix, Ubuntu 6.10, mint, and sabyon. They work in other computers, so I can't just blame the disks. This is becoming worriesome. So long as I keep my RAM usage to under 1 gig or so, everyone is happy, but I want to have 10 apps open at once gosh darn it!

---

### Post by Tango_Down on 2007-11-20
Even after reformating swap, still says I have 0 bytes free on my swap drive. The swap is in the fstab and shows up correctly in Gparted. Any ideas?

---

### Post by taurus on 2007-11-20
Please post

```
sudo fdisk -l
cat /etc/fstab
free
```
Chances are you are using UUID in /etc/fstab for your swap partition but it has now changed.

---

### Post by Tango_Down on 2007-11-20
Seems fstab was changed during my edgy upgrade, but not on any later occasion. fdisk -l shows everything seems to be in order, but it does not list the UUID of the drive. How would I find out what the new UUID was if it has changed?

---

### Post by Tango_Down on 2007-11-20
Here it is if you are curious. 

fdisk 
   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        6374    51199123+  83  Linux
/dev/hdc2            6375        6439      522112+  82  Linux swap / Solaris
/dev/hdc3   *        6440       14088    61440120    7  HPFS/NTFS
/dev/hdc4           14089       18932    38909430   83  Linux

/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc4 -- converted during upgrade to edgy
UUID=a3dc8bbe-a220-46fd-8d55-568181164be7 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdc1 -- converted during upgrade to edgy
UUID=6668cc63-2948-4206-90ac-abad8eea9f0a /media/hdc1 ext3 defaults 0 2
# /dev/hdc3 -- converted during upgrade to edgy
UUID=92CC96A7CC9684DF /media/hdc3 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdc2 -- converted during upgrade to edgy
UUID=a1d17e93-1caa-49f6-9b3b-3d3ec622c848 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0server@WH

---

### Post by taurus on 2007-11-20
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line

```
UUID=a1d17e93-1caa-49f6-9b3b-3d3ec622c848 none swap sw 0 0
```
with this one.

```
/dev/hdc2   none   swap   sw   0   0
```
Save it and reboot.  Now, see if your swap partition is activated.

```
free
```

---

### Post by Tango_Down on 2007-11-21
Righto, problem solved, swap drive active, now all I have to do is open 10 applications to see if that is what was causing Gnome to lock up.

---

