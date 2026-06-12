---
title: "Unable to Format USB drive (Olympus)  (Using mkdosfs)"
date: 2009-02-27
forum: General Help
---

### Post by keyshawn on 2009-02-27
Hi, 

I am trying to format a USB drive (it's actually a Olympus WS-300M, a digital voice recorder, but it acts like a USB drive. It normally mounts to the computer like a typical USB drive). in ubuntu 8.10. At this point, I'm not concerned about recovering any data on the drive. The device has worked with linux smoothly in the past, but the device has become corrupted (not sure how it happened) The device appears in nautilus, but none of the files within the device appear. 

Also, 
The drive does not appear in gparted but it does mount, because: sudo fdisk -l returns: 

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         500      255786    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 44) logical=(0, 6, 12)
```

After doing some searching,
I read [http://ubuntuforums.org/showpost.php?p=4558786&postcount=3](http://ubuntuforums.org/showpost.php?p=4558786&postcount=3)

and followed the directions. 

After unmounting the drive, I issued: sudo mkdosfs -v -F 16 /dev/sdc1
This returned:
```
mkdosfs 2.11 (12 Mar 2005)
mkdosfs: unable to open /dev/sdc1
```


Right now, I'm trying to find other ways to format this USB hard drive.

thanks, 
keyshawn

---

### Post by dannyboy79 on 2009-02-27
the quicket way would be to write all zeros to the drive, then repartition it, the reformat it and start over. try this:
```
dd if=/dev/zero of=/dev/sdc bs=1M
```
of course the drive can't be mounted at the time of running this command

---

### Post by TheForkOfJustice on 2009-02-27
I have a similar problem with my OneTouch USB drive.  I can't do a low-level format either apparently or I just haven't found the tool for it yet.

I managed to delete the partitions that were on it with the gparted LiveCD and it does mount on Windows and Ubuntu if the device remains unpartitioned but you cant re-partition/reformat it with Windows, Ubuntu or the Gparted LiveCD.

---

### Post by keyshawn on 2009-02-27
> **dannyboy79 said:**
> the quicket way would be to write all zeros to the drive, then repartition it, the reformat it and start over. try this:
```
dd if=/dev/zero of=/dev/sdc bs=1M
```of course the drive can't be mounted at the time of running this command

thanks for the quick response ! 

After unmounting again (just to be sure) sudo umount /dev/sdc1

I issued: sudo dd if=/dev/zero of=/dev/sdc bs=1M
and received: 
```
dd: opening `/dev/sdc': Read-only file system
``` :(

---

### Post by dannyboy79 on 2009-02-27
after you think you unmounted, please post the output after entering this command:
```
sudo mount
```

also, let me see your contents of your fstab file, that would be this:
```
sudo cat /etc/fstab
```

if all else fails, restart computer with usb stick (or whatever it is) unplugged. then when you plug it in, show me the results of this command:
```
dmesg | tail
```

---

### Post by keyshawn on 2009-03-03
> **dannyboy79 said:**
> after you think you unmounted, please post the output after entering this command:
```
sudo mount
```
```
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/skorasaurus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=skorasaurus)
/dev/sdc1 on /media/freeagent type ext3 (rw,nosuid,nodev,uhelper=hal)

```(I've rebooted my computer since then, and my external hard drive (freeagent) letter took the point of /dev/sdc1. My USB drive was mounted at /dev/sdd1 at this reboot). 

After I issued the 'sudo mount' (to ensure that it wasn't mounted), 

I issued the 'dd....' command again' and received the the same 'read-only' error that I described in my previous post. 


My fstab is: 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=7d610450-ef9d-469a-9fa7-47d043154614 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=130b90eb-7d81-4119-8f32-d58017f0ffb6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

dmesg | tail returned: 

```

[ 1418.737004] FAT: Filesystem panic (dev sdb1)
[ 1418.737009]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1418.737246] FAT: Filesystem panic (dev sdb1)
[ 1418.737253]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1419.679923] FAT: Filesystem panic (dev sdb1)
[ 1419.679938]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1419.683322] FAT: Filesystem panic (dev sdb1)
[ 1419.683339]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1421.630142] FAT: Filesystem panic (dev sdb1)
[ 1421.630153]     fat_get_cluster: invalid cluster chain (i_pos 0)

```

thanks for your patience,
keyshawn

---

### Post by dannyboy79 on 2009-03-04
I don't see /dev/sdb being used, what is /dev/sdb then?
when you plug in this voice recorder, what does
```
dmesg | grep usb
``` 
return?
and also
```
lsusb
```

---

### Post by keyshawn on 2009-03-05
dmesg | grep usb returns:```
[    6.980024] usbcore: registered new interface driver usbfs
[    6.980050] usbcore: registered new interface driver hub
[    6.981008] usbcore: registered new device driver usb
[    6.989859] usb usb1: configuration #1 chosen from 1 choice
[    7.096565] usb usb2: configuration #1 chosen from 1 choice
[    7.217228] usb usb3: configuration #1 chosen from 1 choice
[    7.425526] usb usb4: configuration #1 chosen from 1 choice
[    7.529398] usb usb5: configuration #1 chosen from 1 choice
[    7.584106] usb 3-1: new high speed USB device using ehci_hcd and address 2
[    7.632511] usb usb6: configuration #1 chosen from 1 choice
[    7.756171] usb usb7: configuration #1 chosen from 1 choice
[    7.756530] usb 3-1: configuration #1 chosen from 1 choice
[    8.092104] usb 7-5: new high speed USB device using ehci_hcd and address 2
[    8.234995] usb 7-5: configuration #1 chosen from 1 choice
[    8.249294] usbcore: registered new interface driver libusual
[    8.256847] usb-storage: device found at 2
[    8.256850] usb-storage: waiting for device to settle before scanning
[    8.256852] usbcore: registered new interface driver usb-storage
[   13.257532] usb-storage: device scan complete
[   18.728278] input: Acer Crystal Eye webcam as /devices/pci0000:00/0000:00:1a.7/usb3/3-1/3-1:1.0/input/input6
[   18.728326] usbcore: registered new interface driver uvcvideo
[13804.881165] usb 5-2: new full speed USB device using uhci_hcd and address 2
[13805.083579] usb 5-2: configuration #1 chosen from 1 choice
[13805.127286] usb-storage: device found at 2
[13805.127301] usb-storage: waiting for device to settle before scanning
[13805.314514] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4811
[13805.314806] usbcore: registered new interface driver usblp
[13810.126773] usb-storage: device scan complete
[13835.922574] usblp0: removed
[55839.588075] usb 4-1: new full speed USB device using uhci_hcd and address 2
[55839.743028] usb 4-1: configuration #1 chosen from 1 choice
[55839.756895] usb-storage: device found at 2
[55839.756902] usb-storage: waiting for device to settle before scanning
[55844.754240] usb-storage: device scan complete
```lsusb returns:

```

Bus 007 Device 002: ID 0bc2:3001 Seagate RSS LLC 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 03f0:4811 Hewlett-Packard PSC 1600
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 07b4:0215 Olympus Optical Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 064e:a103 Suyin Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```I have my printer, an external USB hard drive, and the voice recorder plugged in. I have one other USB port that is not being used. 

thanks for your troubleshooting help,
keyshawn

---

### Post by dannyboy79 on 2009-03-06
does the voice recorder have a SD card in it? if so, is the SD card locked? I know I have many SD cards that have a little lock mechanism that doesn't allow anything to be removed or added to it. Could this be the problem, if not then I am out of ideas here, sorry.

---

### Post by lindsay7 on 2009-03-06
If you get to a windows machine, this tool will clean and format the usb back to factory settings, HP USB Disk Storage Format Tool v2.1.8. Search for it on the internert.

---

### Post by keyshawn on 2009-03-06
thanks for the replies, 

dannyboy79,

It isn't an SD based drive, nor are there are SD slots on the recorder. 

Lindsay7,

I downloaded and installed your recommended program on a windows computer (xp). When *I ran* it to erase the recorder, it said the drive was write protect :(

thank you for your help. I'll try TheForkOfJustice's suggestion next.

---

### Post by Umang on 2010-02-01
> **keyshawn said:**
> thanks for the replies, 

dannyboy79,

It isn't an SD based drive, nor are there are SD slots on the recorder. 

Lindsay7,

I downloaded and installed your recommended program on a windows computer (xp). When *I ran* it to erase the recorder, it said the drive was write protect :(

thank you for your help. I'll try TheForkOfJustice's suggestion next.
Very sorry to revive this, but did you find a solution? I seem to have exactly the same problem (including not being able to format on Windows).

EDIT: Sorry. Ignore this post. I'm posting a new question on the General Help forum.

---

