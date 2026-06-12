---
title: "Please help - moving grub/MBR"
date: 2009-06-04
forum: General Help
---

### Post by Lucky75 on 2009-06-04
Hi all,

So, I had a dual boot going with XP and ubuntu, where XP was on one disk, and I installed Ubuntu overtop on a separate disk. Unfortunately, my XP disk has crashed, and now I cannot boot into anything (typing from a live cd).

I'm a bit shaky with the booting stuff, but from what I understand, my MBR would be on the original XP disk? How would I move it over to a different disk so I can boot?

Thanks!

---

### Post by Lucky75 on 2009-06-04
Oh, and I'm pretty sure that I had my menu.lst file at /boot/grub/menu.lst, but there's no /boot/grub folder anymore. Was that linked from somewhere else?

---

### Post by merlinus on 2009-06-04
If you are booting from the live cd, then your ubuntu partitions are not mounted, so indeed there is no /boot/grub/menu.lst.

---

### Post by SuperSonic4 on 2009-06-04
It would be easier to reinstall grub from a live cd IMO.

Can you post the output of ```
sudo fdisk -l
```

Mine is below if you want to base yours off it, in a terminal type ```
sudo nano /boot/grub/menu.lst
``` and paste the following, changing the drives as necessary:

```
# Config file for GRUB - The GNU GRand Unified Bootloader                                                                                                                                                                                    
# /boot/grub/menu.lst                                                                                                                                                                                                                        

# DEVICE NAME CONVERSIONS 
#                         
#  Linux           Grub   
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,1)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/db6d30e6-de80-49a5-9289-6b32bfa1cbfb ro
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,1)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/db6d30e6-de80-49a5-9289-6b32bfa1cbfb ro
initrd /boot/kernel26-fallback.img

# (2) Windows
title Windows Vista
rootnoverify (hd0,0)
makeactive
chainloader +1

```

---

### Post by Lucky75 on 2009-06-04
Well, I mounted my linux partition. Still doesn't matter though. How can I fix it so I can boot? lol


Edit: Thanks, how would I reinstall grub to my main drive though? And would it allow me to boot directly to the disk/through grub?

I'm a bit shaky on how this stuff really works lol

---

### Post by blueridgedog on 2009-06-04
Here are the instructions for reinstalling grub and the mbr (to the first hard drive, I assume you have removed the dead drive, if not, you may need to alter the install line to go to the second).  If it can't find /boot/grub, which you mentioned in your second post, then you should post the output of sudo fdisk -l so we can see what disks and partitions you have.

Bootup a live cd, open a terminal and do the following.
```

sudo grub
```

This will result in a "grub>" prompt. At grub>. enter these commands
```

find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to use as the source for the new mbr.

Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```
setup (hd0)
```

Note, if you want to put the new mbr in another hard drive, you will need to adjust it accordingly.

Finally exit the grub shell
```

quit
```

---

### Post by Lucky75 on 2009-06-04
So, I think it's sdb1 that's my main partition. Not too sure how that screws up the above commands though. Thanks!

```


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb859511d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c21f78b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       46976   377334688+  83  Linux
/dev/sdb2           59765       60801     8329702+   f  W95 Ext'd (LBA)
/dev/sdb3           46977       59764   102719610    7  HPFS/NTFS
/dev/sdb5           59765       60801     8329671   82  Linux swap / Solaris

Partition table entries are not in disk order


```

```

grub> find /boot/grub/stage1
 (hd1,0)

grub> setup (hd1)

Error 12: Invalid device requested


```

---

### Post by merlinus on 2009-06-04
Looks like you missed the root command.

```

sudo grub
root (hd1,0)
setup (hd1)
quit

```

---

### Post by Lucky75 on 2009-06-04
grub> root (hd1, 0)
Error 11: Unrecognized device string


Is that correct?

---

### Post by merlinus on 2009-06-04
No space between hd1,0

---

### Post by Lucky75 on 2009-06-04
Ok, it worked. Where did that install to? Should I be able to boot back into ubuntu now? 

```

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded

```

I still can't see /boot/grub though, unless not all of it is mounted or something? Will that fix the bootloader and move it onto my ubuntu disk?

Edit: oh, nevermind, I can see grub. I had to cd .. before and refresh.

---

### Post by merlinus on 2009-06-04
grub is now installed in the mbr of your second hdd.  if you boot from that disk first, the menu should appear.  You may need to select that hdd to be first in your bios.

---

### Post by Lucky75 on 2009-06-04
ok, thanks. I'll give it a shot!

---

### Post by blueridgedog on 2009-06-04
Note you can easily use the commands to setup any drive...and as long as you know to tell your system to boot from that drive you should be ok.

---

### Post by VMC on 2009-06-04
It also looks like you don't have an active boot partition. Look under Boot from fdisk output.

---

### Post by Lucky75 on 2009-06-04
Right, what? Lol

It seemed to somewhat work, although grub was pointing to (hda2,0) instead of 0,0. Had to modify that. 

What was that about no active boot partition? How do I set that?

---

### Post by VMC on 2009-06-04
> **Lucky75 said:**
> Right, what? Lol

It seemed to somewhat work, although grub was pointing to (hda2,0) instead of 0,0. Had to modify that. 

What was that about no active boot partition? How do I set that?

I think that's a red herring as someone pointed out before. Because Grub takes control. But you can open up cfdisk to make an Active boot:

```
sudo cfdisk
```

---

### Post by Lucky75 on 2009-06-04
oh, ok. Odd, it says that I only have a /dev/sda1 partition, though I'm on sdb lol.

---

### Post by VMC on 2009-06-05
> **Lucky75 said:**
> oh, ok. Odd, it says that I only have a /dev/sda1 partition, though I'm on sdb lol.

It defaults to first hd. Do the following:

```
sudo cfdisk /dev/sdb
```

---

### Post by Lucky75 on 2009-06-05
That got it, thanks. Not too sure what it does though ;)

---

