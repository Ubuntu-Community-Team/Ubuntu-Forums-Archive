---
title: "My directory is &quot;Not a directory&quot;???"
date: 2009-04-30
forum: General Help
---

### Post by nickstedman on 2009-04-30
A directory shared with VirtualBox, is no longer accessible after recovering from a grub error 17 which required editing the /boot/grub/menu.lst to make it point to my linux partition. The directory is on a different partition. In fact all the files and folders on that partition which are associated with Virtualbox appear as blue diamonds and are not recognized as anything. All I care about at this point is recovering the files from the inaccessible folder. Any help would be appreciated. I am migrating this thread here from this [one]("http://forums.virtualbox.org/viewtopic.php?f=7&t=17189&p=73285#p73285") as it seems to have more to do with the OS...I think??

---

### Post by jazzgossen on 2009-05-01
Please post the output of "sudo fdisk -l" and perhaps also "mount".

---

### Post by nickstedman on 2009-05-01
nicholas@jelly:~$ sudo fdisk -l
[sudo] password for nicholas: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           9       72261    6  FAT16
/dev/sda2              10         270     2096472   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3             271        8915    69432928   83  Linux
/dev/sda4            8916       14594    45616567+   f  W95 Ext'd (LBA)
/dev/sda5           10827       14119    26450988   83  Linux
/dev/sda6           14120       14266     1180736   82  Linux swap / Solaris
/dev/sda7           14267       14594     2620416    c  W95 FAT32 (LBA)

---

nicholas@jelly:~$ mount
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
/dev/sda3 on /media/disk type ext3 (rw,relatime)
none on /proc/bus/usb type usbfs (rw,devgid=46,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nicholas/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nicholas)
/dev/scd0 on /media/XP2_PER_ENG type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)

---

### Post by nickstedman on 2009-05-01
And here is the output of ls -la

nicholas@jelly:/media/disk$ ls -la
ls: VBox: Input/output error
total 3961848257
drwxrwxrwx    12 root       root                      4096 2009-04-30 18:39 .
drwxr-xr-x     4 root       root                      4096 2009-05-01 18:53 ..
drwxrwxrwx     2 root       root                      4096 2009-04-26 07:32 dev
drwxrwxrwx     2 root       root                     16384 2007-10-11 21:01 lost+found
drwxrwxrwx     3 nicholas   nicholas                  4096 2008-04-02 20:39 Music
drwxrwxrwx     2 root       root                      4096 2009-04-26 07:32 proc
---Sr-S-w-  1795 2867168839   15062318 2026646492708272234 1986-07-19 22:11 .Trash-1000
drwxrwxrwx    23 nicholas   nicholas                  4096 2008-09-30 08:50 .Trash-nicholas
?rwxrwxrwx    68      29256      12290          2684551289 1970-01-07 06:28 VBox
?r-xr-S-wT 27246 1414883941 1128674938          1718169634 2037-10-12 09:53 .VirtualBox
drwxrwxrwx     4 nicholas   nicholas                  4096 2009-05-01 18:17 vm
cr-sr-S--- 53995  448454453 2665249648             50, 133 1926-10-04 06:37 VMshare2

The permissions are crazy.
VMshare2 is the folder I want to recover...

Does anyone have any ideas??

---

