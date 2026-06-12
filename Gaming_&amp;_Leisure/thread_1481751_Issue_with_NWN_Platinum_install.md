---
title: "Issue with NWN Platinum install"
date: 2010-05-12
forum: Gaming &amp; Leisure
---

### Post by Elvish Legion on 2010-05-12
Not sure if this should go here or go in the hardware section but I'm having an issue with the NWN install script.

I get to the part where you point to your dvd drive and it says invalid drevice

I think it is an issue with my fstab but not 100% sure

fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7cf8e291-cd9c-495b-8122-5586cf40f242 none            swap    sw              0       0
```
```

sudo lshw -C disk 
  *-disk                  
       description: ATA Disk
       product: ST980411ASG
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: DE13
       serial: 5TF020TY
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00063e30
  *-cdrom
       description: DVD-RAM writer
       product: DVD+-RW TS-U633A
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/_DVD
       version: D200
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/_DVD
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted
```

Probably would have been better in hardware but fixed it

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7cf8e291-cd9c-495b-8122-5586cf40f242 none            swap    sw              0       0
/dev/sr0  	/cdrom  	auto  	ro,noauto,user,exec  
```

Ubuntu for what ever reason has the cd just in the / area instead of /mnt or /media

---

