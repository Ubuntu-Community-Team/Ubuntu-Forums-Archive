---
title: "FAT32 USB flash drives always mount as root, read only as user"
date: 2014-11-02
forum: Desktop Environments
---

### Post by wandrson on 2014-11-02
At some point in the past, my desktop machine has stopped allowing read/write access to any of the usb flash drives (formatted FAT32).

They all default to root user ownership, and require root access to write to the drive.

I have scoured the web for similar problems, which I have found, but none of the solutions seem to correct my problem.

One solution that seemed to offer some possibility was to reformat the drive from my ubuntu machine.  That worked, until I rebooted the machine and then it went back to the default behavior of read only for the non-root user.

I am now starting to use several encrypted usb flash drives and can not reformat them.  They work on other ubuntu machines, but not the one on my desktop.

Any suggestions

Oh, I also get this window when I connect the drive, but it is still accessible from the root account

[IMG]https://drive.google.com/file/d/0B-kiKiYKrSl9akR2OEJmS1NpeU0/view?usp=sharing[/IMG][https://drive.google.com/file/d/0B-kiKiYKrSl9akR2OEJmS1NpeU0/view?usp=sharing](https://drive.google.com/file/d/0B-kiKiYKrSl9akR2OEJmS1NpeU0/view?usp=sharing)

---

### Post by mc4man on 2014-11-02
You may want to - 
post what release of Ubuntu, the current & recent default for external/removable  media is to mount to /media/username/volume label or UUID
Post contents of /etc/fstab
And just to see, should return nothing - 
```
cd
ls -l | grep root
```

---

### Post by wandrson on 2014-11-03
Thanks! 

I am currently running release 14.04; however, this machines started our with 11.10 and has gone through regular updates.  This problem first showed up with 13.?  about a year ago.

When I first format a usb flash drive it will mount under /media/username/volume label  however, the next time I plug it in it mounts as root access under /media/usb#

my fstab
> 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f765eb57-02f8-457e-b55c-d191aa5a8245 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8a2adc17-6d56-4a68-952e-4e227c16547e none            swap    sw              0       0
# Additional drive mounts
/dev/sdb /home/wandrson ext4 defaults 0 0
/dev/sdc /media/EXP01 ext4 defaults 0 0
/dev/sdd /home/wandrson/Public ext4 defaults 0 0 
#usbfs for virtualbox
#none /proc/bus/usb usbfs devgid=125,devmode=664 0 0


sda is a sata ssd, and sdc, sdb, sdd are 2TB sata drives
and the results from your code snippet are
> wandrson@delphi:~$ cd
wandrson@delphi:~$ ls -l | grep root
-rw-r--r--  1 root     root       88976591 Nov  1 12:30 file.list.txt
drwxr-xr-x  5 wandrson root           4096 Apr 28  2014 kicad_sources
wandrson@delphi:~$ 



---

