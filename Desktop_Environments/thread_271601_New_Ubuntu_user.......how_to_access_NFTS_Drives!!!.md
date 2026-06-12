---
title: "New Ubuntu user.......how to access NFTS Drives!!! (Solved)"
date: 2006-10-04
forum: Desktop Environments
---

### Post by jonathanphippen on 2006-10-04
Hello, I am a new Ubuntu user. I would love to switch full time to linux, but I still would like to access my NFTS drives, is there a way? I have been using Gnome ubuntu, I have little exp. with command lines, please help me!!!
Many some educational resources would help as well. Thank you

---

### Post by Locomotion on 2006-10-04
hm
I'm also new to linux

1st= you must know that linux can't modify NTFS partition, just see, etc...
2nd= When I installed Ubuntu, it mounted all my partitions with the right permissions.

Sorry, I don't know how to mount manually, all I know is that something with fstab...

Wait someone expert come here to help :P


**EDIT:**
I found in Ubuntu Br guide.

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

/media/windows is a exemple of where you want to mount
/dev/hda1 is the partition you want to mount, you need to check what is the name of your partition

**EDIT2:**
Ahh... to mount everytime you boot is:
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

add in fstab:
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
save

same rules for the edit1

---

### Post by Fingerlakes_Dave on 2006-10-04
Same issue here.
 See my post:
 Question  Drives on desktop - how?  

 Similar issue for sure.  I can get my main drive (C) and the ntfs and ext3 partitions, however, I cam't view anything else.
 I also can't figure out how to mount them.

 ](*,) ](*,)

---

### Post by Brooze on 2006-10-05
if you aren't familiar with fstab, you can make a boot script to do the same..

mount -o umask=0022 <drive path> <mount path>

example (my own personal boot script)
mount -o umask=0022 /dev/hdb1 /home/mike/Storage

Make sure you unmount the drive umount <drive path> first if it is already mounted... and you have to be root...

---

### Post by aysiu on 2006-10-05
For future reference, here are some tutorials on mounting partitions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

If you want it to automatically appear on the desktop, mount it within the /media folder

**Will appear on desktop**
/media/windows

**Will not automatically appear on desktop**
/windows

---

### Post by weird_c00kie on 2006-10-05
infinite thanks for that aysiu. i got my drives working at last :D

---

### Post by Aualin on 2006-10-05
to get wirte support folliw this guide
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by Fingerlakes_Dave on 2006-10-05
> **aysiu said:**
> For future reference, here are some tutorials on mounting partitions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

If you want it to automatically appear on the desktop, mount it within the /media folder

**Will appear on desktop**
/media/windows

**Will not automatically appear on desktop**
/windows

  MAny thanks for these links!

---

### Post by jonathanphippen on 2006-10-05
Thankx for the tips!

---

### Post by weird_c00kie on 2006-10-11
strange.....
i had some issues with my drives, so i ended up having to reinstall ubutu AGAIN (3rd time now), but somewhere along the way, my XP drive got screwed up and i can't boot off it anymore.

when i try mounting it through linux, it's different to what the psychocats.net guide shows.

when i use the fdisk -1, i get this:

> Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       38538   309556453+  83  Linux
/dev/hda2           38539       38913     3012187+   5  Extended
/dev/hda5           38539       38913     3012156   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24321   195358401    7  HPFS/NTFS

the ntfs drive is separated. 

when i use *sudo nano /etc/fstab* i get this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw         O5D     0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

with the ntfs drive completely missing

anyone have any idea what's going on? :(

---

### Post by weird_c00kie on 2006-10-11
nevermind... i followed Locomotion's instructions and got it working :D

---

### Post by weird_c00kie on 2006-10-11
what tha..... and now it doesn't work again.... ubuntu seems to like messing itself up everytime i shut down and boot up again

---

