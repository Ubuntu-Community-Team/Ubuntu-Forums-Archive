---
title: "ubuntu  not displaying at startup menu"
date: 2009-04-27
forum: General Help
---

### Post by kask1984 on 2009-04-27
hi every one ,
i have installed ubuntu8.10 in windows xp using wubi.it was working fine for me but one day windowsxp got one probelm .it was unable to boot into xp as boot.ini file was missing.i solved that problem by reparing windows xp.since then my system is not displaying  ubuntu at startup(infact it is not at all displaying startup menu).
how can i get back ubuntu at start up.
how can i access ubuntu partition from windows xp(i tried this but not working) or using ubuntu live cd ( i tried this also ,but it also not working).
actually i have backedup material about 6gb in ubuntu .now i am unable to access this.
please help me .
thanks a lot  in advance.

---

### Post by akudewan on 2009-04-27
Try this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by sahabcse on 2009-04-27
Hi 

follow below url for fixing the grub issue.

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)

---

### Post by kask1984 on 2009-04-27
reply to akudewan and sahabcse

Error 15: File not found
 this is the message i am getting after executing "find /boot/grub/stage1"

reply to Ellen2

i have installed ubuntu in separate drive

---

### Post by sahabcse on 2009-04-27
If you installed a /boot partition, do 


#find /grub/stage1

---

### Post by kask1984 on 2009-04-27
this is message i am getting

grub> #find /grub/stage1

Error 27: Unrecognized command

grub> find /grub/stage1

Error 15: File not found

---

### Post by sahabcse on 2009-04-27
Have you logged the grub terminal using

sudo grub

---

### Post by kask1984 on 2009-04-27
yes

---

### Post by sahabcse on 2009-04-27
ok. paste the o/p of sudo mount, sudo fdisk -l, df -h

---

### Post by kask1984 on 2009-04-27
**output of sudo mount**

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda8 on /media/1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/KNERG type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


**output of sudo fdisk**

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...


**output of df -h**

Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 504M  2.0M  502M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 504M  2.0M  502M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 504M     0  504M   0% /lib/init/rw
varrun                504M  100K  504M   1% /var/run
varlock               504M     0  504M   0% /var/lock
udev                  504M  2.8M  501M   1% /dev
tmpfs                 504M  104K  504M   1% /dev/shm
rootfs                504M   37M  468M   8% /
/dev/scd0             699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 504M   12K  504M   1% /tmp
/dev/sda8              32G   15G   18G  46% /media/1
/dev/sda7              30G   11G   20G  35% /media/disk
/dev/sdb1             3.9G  3.4G  452M  89% /media/KNERG

---

### Post by kask1984 on 2009-04-27
**output of sudo mount**

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda8 on /media/1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/KNERG type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


**output of sudo fdisk**

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...


**output of df -h**

Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 504M  2.0M  502M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 504M  2.0M  502M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 504M     0  504M   0% /lib/init/rw
varrun                504M  100K  504M   1% /var/run
varlock               504M     0  504M   0% /var/lock
udev                  504M  2.8M  501M   1% /dev
tmpfs                 504M  104K  504M   1% /dev/shm
rootfs                504M   37M  468M   8% /
/dev/scd0             699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 504M   12K  504M   1% /tmp
/dev/sda8              32G   15G   18G  46% /media/1
/dev/sda7              30G   11G   20G  35% /media/disk
/dev/sdb1             3.9G  3.4G  452M  89% /media/KNERG

---

### Post by sahabcse on 2009-04-27
hi

When ever we give the mount command we can find / partition mounted disk. But its not showing ur output. Can u paste the o/p of following

vim /boot/grub/menu.lst
fdisk -l

---

### Post by kask1984 on 2009-04-27
sorry for late reply, here net has gone

i am not able to follow u r above two commands

when i type first command i got

E325: ATTENTION
Found a swap file by the name "/var/tmp/menu.lst.swp"
          owned by: ubuntu   dated: Mon Apr 27 14:45:46 2009
         file name: /boot/grub/menu.lst
          modified: YES
         user name: ubuntu   host name: ubuntu
        process ID: 8211
While opening file "/boot/grub/menu.lst"

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /boot/grub/menu.lst"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/var/tmp/menu.lst.swp"
    to avoid this message.
"/boot/grub/menu.lst" [New DIRECTORY]
Press ENTER or type command to continue

if i press enter it is showing something (which i am not able to follow)

---

### Post by kask1984 on 2009-04-27
i haven't installed ubuntu using wubi in whole drive .i installed in a folder of 10 gb

---

### Post by sahabcse on 2009-04-27
sudo vim /boot/grub/menu.lst

Then press enter for opening the file

sudo fdisk -l

---

### Post by kask1984 on 2009-04-27
hi 
 when i typed first command i am getting the output as

~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"/boot/grub/menu.lst" [New DIRECTORY]

then i am unable to type  anything 

here net is too slow thats why late reply

in the process of finding solution to my probelm i did not take lunch 

please suggest me one solution i am leaving now 

thanks bye

---

