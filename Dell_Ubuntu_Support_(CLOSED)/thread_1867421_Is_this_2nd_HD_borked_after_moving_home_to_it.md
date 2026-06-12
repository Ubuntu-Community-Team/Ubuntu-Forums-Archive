---
title: "Is this 2nd HD borked after moving home to it?"
date: 2011-10-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by c4c on 2011-10-22
Let me preface my problem by saying I had Ubuntu 10.04.3 on an original 20 GB HD and using Gparted, and instructions from [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) I added a 40 GB HD and moved home to it.

I have done this to 3 other of the same machines (Dell Optiplex GX240s, all with Ubuntu 10.04.3 on the original 20 GB HDs) adding a 20 GB to one, an 80 GB HD to the last two, moving home to the larger drive and deleting the old home on each.

The only difference (or maybe no-no?) I can think of with this add-2nd-drive-move-home-to-it is installing the security updates immediately after deleting the home_old from the 20 GB on this machine. Also, I believe this was the first one I did not install and run pysdm to hide the sdb1 drive without going back into fstab.

Everything seemed okay until I innocently double-clicked OOo Draw and it froze on the splash screen. I was still able to move the mouse and drop down the Places menu when the whole machine froze.

I rebooted and was greeted with this:

```
Gave up waiting for root device.  Common problems:

-Boot args (cat /proc/cmdline)
     -Check rootdelay= (did the system wait long enough?)
     -Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; 1s /dev)
ALERT!  /dev/disk/by-uuid/7b4c9802-1da4-4e38-869b-05eaabbbe13 does not exist.
Dropping to a shell!
 
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built in commands.
 
(initramfs)
```hangs here for a minute or two and then continues

```
udevd[66]: worker [76] unexpectedly returned with status 0x0100
 
udevd[66]: worker [76] failed while handling '/devices/pci0000:00/0000:00:1f.1/host0/target0:0:1/0:0:1:0/block/sdb/sdb1'
```I rebooted from a Ubuntu 10.04.2 LiveCD, got a sting or errors all having to do with my 2nd drive (sdb1) it seemed, buffer I/O errors, failed command=Read DMA, logical block 5 and 6 and 7 [sorry these went by fairly quickly] but after like 10 minutes it booted up from the LiveCD.

I went to Terminal and did

sudo fdisk -l

Output follows

```
Disk /dev/sda: 20.0 GB, 20396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 822528 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006f06f

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2327 18689024 83 Linux
/dev/sda2 2327 2434 859137 5 Extended
/dev/sda5 2327 2324 859136 2 Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ebf69

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 4865 39078081 83 Linux

ubuntu@ubuntu:~$
```Then I went to Gparted and tested sdb1; gparted_details.htm follows:

```
GParted 0.5.1

Libparted 2.2
Check and repair file system (ext4) on /dev/sdb1  00:02:17    ( ERROR )
         
calibrate /dev/sdb1  00:01:33    ( SUCCESS )
         
path: /dev/sdb1
start: 63
end: 78156224
size: 78156162 (37.27 GiB)
check file system on /dev/sdb1 for errors and (if possible) fix them  00:00:44    ( ERROR )
         
e2fsck -f -y -v /dev/sdb1
         
Could this be a zero-length partition?
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1 
```Sorry if I am missing something obvious. Anyone have a suggestion, or some other output I should be including? Thanks!

---

### Post by c4c on 2011-10-24
Bad HD. Didn't notice before. :rolleyes: Sorry to bother anyone.

---

