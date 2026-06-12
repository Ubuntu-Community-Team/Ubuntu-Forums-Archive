---
title: "finding unmounted partitions"
date: 2009-04-24
forum: General Help
---

### Post by joelswatson on 2009-04-24
heya,

i have just installed 9.04 on my laptop, and i am a bit lost how to find my other partitions, i have 2 500gb hard drives, and i set them up as follows

drive 1 (500gb)

/ 200gb
/home 100gb
/swap 4gb
/usr 50gb

drive 2 (500gb)
/ 500gb

it was something like that,

but i cant find the other partitions

i was hoping to find out how to mount them, so i can start copying back stuff from my external hard drive

thanks

---

### Post by kanikilu on 2009-04-24
You should be able to see your partitions in gparted or with ```
sudo fdisk -l
``` (lowercase "L", not "one")

By the way, which is your actual root partition? You listed "/" on each drive...

---

### Post by joelswatson on 2009-04-24
heya, this is the output for the fdisk command, how do i mount them, and access them like you can partitions in windows.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ed4bd0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24328   195414628+  83  Linux
/dev/sda2           24329       60801   292969372+   5  Extended
/dev/sda5           30408       60801   244139805   83  Linux
/dev/sda6           29909       30406     4000153+  82  Linux swap / Solaris
/dev/sda7           24329       29907    44813254+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ed4bd04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux




/dev/sda1   *           1       24328   195414628+  83  Linux (ubuntu)
/dev/sda5           30408       60801   244139805   83  Linux (torrent)
/dev/sda6           29909       30406     4000153+  82  Linux (swap)
/dev/sda7           24329       29907    44813254+  83  Linux (personal files)

and the second drive i want it mounted as just 1 partition with the name storage,

how do i do that.

thanks

---

### Post by kanikilu on 2009-04-24
There are pretty much two ways to do this. You can use a GUI mount manager such as PySDM ([http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)), or manually edit fstab.

To do it manually, for the second disk, first create a mountpoint:
```
sudo mkdir /media/storage
```

Next, find the UUID of that drive - this isn't entirely necessary since you know the device name (/dev/sdb1), but it's not a bad idea since you have so many partitions:
```
ls -l /dev/disk/by-uuid/ | grep sdb
```

The number you want is going to be a long alpha-numeric string, for example:
```
6975ad8e-561b-4ac7-8613-caac907c8c66
```

Copy the UUID or write it down.

Now open /etc/fstab as root:
```
gksu gedit /etc/fstab
```

First, check to make sure /dev/sdb1 or the UUID found above is not already in there - if it is, see if it's already mounted in the mountpoint listed. If it's not already in there, you can add a new line:
```
UUID=6975ad8e-561b-4ac7-8613-caac907c8c66 /media/storage ext3 defaults 0 0
``` Save and close the file.

Notes:
* Don't leave a blank line at the end of the file
* Substitute your UUID instead of the example (obviously)
* I'm guessing here that sdb1 is ext3, gparted should tell you exactly what it is
* Wherever you see a space in the example line above, use a tab instead
* Don't reboot until you run **sudo mount -a**, if it returns an error, it needs to be fixed first. If it's successful, it shouldn't return any output and you should be able to browse your drive by going to /media/storage in the file manager (nautilus) or from the terminal.

---

### Post by joelswatson on 2009-04-25
heya, i gave it a shot, and for some reason when i rebooted i couldnt use my keyboard and mouse to login into gnome. so i have gone and done another format and reinstall (which i didnt mind) so now i have a 200gb partition a 4gb swap and 296gb torrent partition for drive 1 and 500gb partition for drive 2. how do i put names on the partitions?

---

