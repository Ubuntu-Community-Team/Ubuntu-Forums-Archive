---
title: "cant see 2nd HDD and firefix problem"
date: 2009-02-20
forum: General Help
---

### Post by razy60 on 2009-02-20
I have a minor problem that if or when i boot into xubuntu i cant seem to find my secondary HDD, If i boot into Ubuntu i just go to places and there it is i think its there in Kubuntu.  Any ideas?

Second issue i have is that when i boot Ubuntu and use firefox after a while i keep getting script errors which i dont get in xubuntu. Is this related in any way to the fact that my graphics card is on its way out, I ask as xubuntu is supposed to be lighter on graphics.

Thanks 


Raz

---

### Post by taurus on 2009-02-20
While in Xubuntu, open a terminal and post the outputs of these commands.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by razy60 on 2009-02-20
here are the results:
 
claudio@claudio-desktop:~$ sudo fdisk -l
[sudo] password for claudio: 

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08a026b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9598    77095903+  83  Linux
/dev/sda2            9599       10011     3317422+   5  Extended
/dev/sda5            9599       10011     3317391   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4863    39062016    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS
claudio@claudio-desktop:~$ sudo blkid
/dev/sda1: UUID="2a836ee9-5b8a-40d8-a0bf-3a40769e4c18" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="962802f0-c9cf-4d1d-aeaf-1c8df9dd9a02" 
/dev/sdb1: UUID="7A149D17149CD789" TYPE="ntfs" 
/dev/sdc1: UUID="02D840E4D840D795" LABEL="New Volume" TYPE="ntfs" 
claudio@claudio-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2a836ee9-5b8a-40d8-a0bf-3a40769e4c18 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=962802f0-c9cf-4d1d-aeaf-1c8df9dd9a02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
claudio@claudio-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              73G  9.3G   60G  14% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  100K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1009M   1% /dev
tmpfs                1012M   24K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdc1             299G   45G  254G  16% /media/New Volume
claudio@claudio-desktop:~$ 

I can see the drive, sdb 40 GB is the one that is missing, sda 82 GB is the one i am using, sdc 320 GB is an external usb drive.

Raz

---

### Post by taurus on 2009-02-20
1.  Try mounting /dev/sdb1 from a terminal with

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

2.  Or if you want it to mount automatically each time you boot, then you need to edit /etc/fstab

```
gksudo mousepad /etc/fstab
```
and add this line to the end of it.

```
UUID=7A149D17149CD789   /media/sdb1   ntfs-3g  defaults,locale=en_US.UTF-8   0   0
```
Save it and close down the mousepad editing window.  Don't forget to create the new mount point for /dev/sdb1.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```

---

### Post by razy60 on 2009-02-20
if i try 

Code:

sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h

this is what i get
claudio@claudio-desktop:~$ sudo mkdir /media/sdb1
mkdir: cannot create directory `/media/sdb1': File exists
claudio@claudio-desktop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
fuse: mount failed: Device or resource busy
claudio@claudio-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              73G  9.2G   60G  14% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  100K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.7M 1009M   1% /dev
tmpfs                1012M     0 1012M   0% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1              38G   87M   38G   1% /media/sdb1
claudio@claudio-desktop:~$ 

i tried the automount which seemed to work but when i look for the drive still cant see it.

Thanks for the help so far

Raz

---

### Post by taurus on 2009-02-20
```
ls -la /media/sdb1
```

---

### Post by razy60 on 2009-02-20
result of your post

claudio@claudio-desktop:~$ ls la /media/sdb1
ls: cannot access la: No such file or directory
/media/sdb1:
$RECYCLE.BIN  store  System Volume Information
claudio@claudio-desktop:~$ 

cheers 

Raz

---

### Post by taurus on 2009-02-20
You forgot the minus sign, ls **[COLOR="Red"]-[/COLOR]**la, but it looks like /dev/sdb1 is now mounted to /media/sdb1 to me.

```
ls -la /media/sdb1
```

---

### Post by razy60 on 2009-02-20
result from my corrected input

claudio@claudio-desktop:~$ ls -la /media/sdb1
total 12
drwxrwxrwx 1 root root 4096 2009-02-15 18:49 .
drwxr-xr-x 5 root root 4096 2009-02-20 19:05 ..
drwxrwxrwx 1 root root 4096 2009-02-10 16:31 $RECYCLE.BIN
drwxrwxrwx 1 root root    0 2009-02-15 18:49 store
drwxrwxrwx 1 root root    0 2009-01-31 13:35 System Volume Information
claudio@claudio-desktop:~$ 

cheers

Raz

---

### Post by razy60 on 2009-02-20
Just checked in KDE and GNOME the drive is in both but now it wont let me unmount it in either.

Just checked a media file in file system and found it along with my cd drive. just got to figure how to unmount it and all will be fine. 

**[COLOR="Red"]BIG THANKS[/COLOR]**

Now just to solve the Firefox problem get a new graphics card and finish 2 bottles of excellent Zinfandel and all will be good.

Thanks again

Raz

---

### Post by taurus on 2009-02-20
If you want to unmount it, just run

```
sudo umount /media/sdb1
df -h
```

---

### Post by razy60 on 2009-02-20
Taurus

Again thanks for the help

Raz

---

