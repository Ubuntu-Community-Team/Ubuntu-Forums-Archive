---
title: "USB External HDD read only.."
date: 2009-02-28
forum: General Help
---

### Post by demothen on 2009-02-28
Today I bought a 320g Seagate USB 2.0 drive in order to attempt to recover some data from my desktop.  I immediately reformatted it to ext3, which I don't think mounted.  I've tried fat32 and ext2, both of which will sometimes mount, but I am unable to write to the disk.  I've played with my permissions, and attempted to log on as root, to no avail.  I just tried a check process via GParted on my laptop, no luck still. It's currently set to ext3.  (I really don't know which format to use, I'm not super concerned about windows usage right now, just really would like to get data off my desktop)  Are there any other suggestions?  I've been using the GUI mount process, is there a manual process I should be using instead?  All I want to do is plug this into my desktop and try to pull a copy of some large folders off a non-booting ubuntu partition (I seem to have broken it while trying to install Jaunty as a second partition, I'm afraid to try much to fix it until I get a better backup - though I do have all essential files, I'd rather not spend a weekend tweaking and installing again)...
Thanks much for any input.

---

### Post by taurus on 2009-02-28
Do you know where that drive is currently been mounted to, mount point?  

```
df -h
```
Let's assuming it's mounted to /media/sdb1 and your login name is demo, you can change the ownership of /media/sdb1 from root to your login name so you can write to it anytime you want.

```
sudo chown -R demo:demo /media/sdb1
ls -la /media
```

---

### Post by demothen on 2009-02-28
You're my hero!

It was mounted to /media/disk...Any way to change the owner automatically, each time I mount the drive?
Thanks!

---

### Post by taurus on 2009-02-28
Well, you need to add an entry in /etc/fstab for your external drive (using the UUID of that drive) but use the noauto,user option so the system doesn't try to mount it at boot.  That way, you can force the system to mount to a particular place, mount point, with you already the owner. 

You first need to know the UUID of that external drive since you need to use it instead of /dev/sdb1.

```
sudo blkid
```
Then, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
UUID=whatever-letters-numbers   /media/sdb1   ext3   noauto,user   0   0
```
Save it and then create the new mount point.

```
sudo mkdir /media/sdb1
```
Now, change the ownership of that new mount point from root to your login name.

```
sudo chown -R demo:demo /media/sdb1
```

---

### Post by demothen on 2009-02-28
Great, thanks! I'll try that one in a bit..Working on getting my documents from my primary partition to that new drive..Do you have any idea what I should do to fix this message?
GParted 0.4.3

Libparted 1.8.8
Check and repair file system (ext3) on /dev/sda1  00:00:00    ( ERROR )
     	
calibrate /dev/sda1  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 508810679
size: 508810617 (242.62 GiB)
check file system on /dev/sda1 for errors and (if possible) fix them  00:00:00    ( ERROR )
     	
e2fsck -f -y -v /dev/sda1
     	
The filesystem size (according to the superblock) is 76626025 blocks
The physical size of the device is 63601327 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes

e2fsck 1.41.4 (27-Jan-2009)
I'm getting it when I try to use Gparted to check my primary partition...Also getting the same message when I try to boot into my primary ubuntu install (8.10) after installing 9.04 to the same drive on a new partition. 

Thanks again.

---

### Post by taurus on 2009-02-28
What's the output of this command?

```
sudo fdisk -lu
```

---

### Post by demothen on 2009-02-28
Disk /dev/sda: 320 GB, 320070320640 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625137345 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          63   508810679   254405308   83  Linux
/dev/sda2       508810680   625137344    58155300    5  Extended
/dev/sda6       508810806   608654654    49913955   83  Linux
Warning: Partition 6 does not end on cylinder boundary.
/dev/sda7       608654718   613008269     2168775   82  Linux swap
Warning: Partition 7 does not end on cylinder boundary.
/dev/sda5       613008333   625137344     6056505   82  Linux swap
Warning: Partition 5 does not end on cylinder boundary.

Disk /dev/sdb: 320 GB, 320070320640 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625137345 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1              63   625137344   312568641   83  Linux

---

### Post by taurus on 2009-02-28
> **demothen said:**
> Disk /dev/sda: 320 GB, 320070320640 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625137345 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          63   508810679   254405308   83  Linux
/dev/sda2       508810680   625137344    58155300    5  Extended
/dev/sda6       508810806   608654654    49913955   83  Linux
**[COLOR="Red"]Warning: Partition 6 does not end on cylinder boundary.[/COLOR]**
/dev/sda7       608654718   613008269     2168775   82  Linux swap
**[COLOR="Red"]Warning: Partition 7 does not end on cylinder boundary.[/COLOR]**
/dev/sda5       613008333   625137344     6056505   82  Linux swap
**[COLOR="Red"]Warning: Partition 5 does not end on cylinder boundary.[/COLOR]**

Disk /dev/sdb: 320 GB, 320070320640 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625137345 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1              63   625137344   312568641   83  Linux

You should consider fixing those.  You cannot use gparted from Ubuntu because you cannot resize a partition while you are using it.  Therefore, you have to use gparted from Ubuntu LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

---

### Post by demothen on 2009-02-28
Okay, I booted into gparted using my intrepid live disk, and ran check on sda6, that ran fine but I am still getting errors when I try to boot. (superblock or partition table likely corrupt message)  I ran the fdisk -lu again, and got these results:
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00003f73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   508810679   254405308+  83  Linux
/dev/sda2       508810680   625137344    58163332+   5  Extended
/dev/sda5       613008333   625137344     6064506   82  Linux swap / Solaris
/dev/sda6       508810806   608654654    49921924+  83  Linux
/dev/sda7       608654718   613008269     2176776   82  Linux swap / Solaris

Partition table entries are not in disk order

Should I Just try to delete the new partition and get back to only one partition?  I'm not really concerned about the second partition, I can play with Jaunty later on with a second drive.

---

### Post by taurus on 2009-02-28
If you look at gparted, you will see there are small "unallocated" spaces between your logical partitions.  You need to expand those partitions so they begin and end where they should be.

---

### Post by demothen on 2009-02-28
I guess I'm not following you there.  I don't have any image hosting right now, so I cant post a screenshot, but this is what I'm looking at in GParted right now.```

partition        filesystem     size            used      unused      flags
/dev/sda1        ext3           242.62 GiB                            Boot
/dev/sda2        extended        55.47 GiB      17.00 GiB 30.61 GiB     
   /dev/sda6     ext3            47.61 GiB      
   /dev/sda7     linux-swap       2.06 GiB  
   /dev/sda5     linux-swap       2.08 GiB

```
I dont see any unallocated space, or any gaps on the graphic...Should I be using a text based version of gparted maybe?

---

### Post by taurus on 2009-02-28
You don't need an image hosting site.  When you reply, scroll down and you will see an attachment button.  Click that and browse to where your screenshot is and upload it from there.

---

### Post by demothen on 2009-02-28
Oops..missed that..

---

