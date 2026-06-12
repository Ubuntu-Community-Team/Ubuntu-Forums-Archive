---
title: "On Natty - problem using 500 GB usb seagate HD"
date: 2011-09-19
forum: Desktop Environments
---

### Post by chandru4895 on 2011-09-19
Upgraded to 11.04 Natty Nahrwal recently. Have purchased a seagate 500 GB external HD mounted on USB. Done one primary & 2 logical partitions. Drives are mounting. Owner shows up as root. Unable to use the disk atall. Can anyone help please?
chandru4895@chandru4895-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0bc2:5021 Seagate RSS LLC 
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 046d:09a4 Logitech, Inc. QuickCam E 3500
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
chandru4895@chandru4895-desktop:~$ 
chandru4895@chandru4895-desktop:~$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda5 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chandru4895/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chandru4895)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
/dev/sdg1 on /media/ExtLinux1 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdg5 on /media/ExtLinux2 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdg6 on /media/ExtLinux3 type ext4 (rw,nosuid,nodev,uhelper=udisks)
chandru4895@chandru4895-desktop:~$

---

### Post by chandru4895 on 2011-09-20
After much searching found appropriate "chown" & "chmod" commands & able to use all partitions OK:)

---

