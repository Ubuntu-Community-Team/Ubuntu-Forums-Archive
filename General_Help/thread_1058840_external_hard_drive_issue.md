---
title: "external hard drive issue"
date: 2009-02-03
forum: General Help
---

### Post by metalmaniac248 on 2009-02-03
i am running ibex, i have an external HDD that is called "My Book" 

when i mount my HDD it puts 2 folders in the media directory, one is called "My Book" and this is the normal one that has allways been there, the other that has only recently appeared is called "My Book_" 

what is this folder and how would i go about removing it?

PS. it seems that the "My Book_" folder is the one that is automatically opened when i access the external HDD from my guest acount, and it says that the "My Book_" folder is owned by guest, i tried > sudo chown -R nick My\ Book_ to change that but it was disallowed

---

### Post by taurus on 2009-02-03
What fillesystem is your external drive?

```
sudo fdisk -l
```

---

### Post by metalmaniac248 on 2009-02-03
ntfs

---

### Post by taurus on 2009-02-03
Both ntfs & fat32 don't play well with permissions (chmod) and ownerships (chown).

---

### Post by metalmaniac248 on 2009-02-03
ok

do you have any idea how i can get rid of this folder?

---

### Post by taurus on 2009-02-03
Make sure you are in the directory (mount point) where you mounted that external harddrive, then post the output of this command.

```
ls -la
```

---

### Post by metalmaniac248 on 2009-02-03
> nick@nick-desktop:/media$ ls -la
total 52
drwxr-xr-x  5 root  root  4096 2009-02-03 13:42 .
drwxr-xr-x 20 root  root  4096 2009-01-30 22:56 ..
lrwxrwxrwx  1 root  root     6 2009-01-30 22:14 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2009-01-30 22:14 cdrom0
-rw-r--r--  1 root  root   114 2009-02-03 13:42 .hal-mtab
-rw-------  1 root  root     0 2009-02-03 13:19 .hal-mtab-lock
drwx------  4 nick  root  4096 2009-02-02 18:46 My Book
drwx------  3 guest root 32768 1970-01-01 01:00 My Book_
nick@nick-desktop:/media$ 
 .

---

### Post by taurus on 2009-02-03
What happens when you run this command to remove it?

```
sudo rm -rf "My Book_"
```

---

### Post by metalmaniac248 on 2009-02-03
> nick@nick-desktop:/media$ sudo rm -rf My\ Book_
[sudo] password for nick: 
rm: cannot remove directory `My Book_': Device or resource busy
nick@nick-desktop:/media$ 
.

---

### Post by taurus on 2009-02-03
Post the output of this then.

```
df -h
```

---

### Post by metalmaniac248 on 2009-02-03
> nick@nick-desktop:/media$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             408G   66G  322G  17% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  552K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  2.9M  1.8G   1% /dev
tmpfs                 1.8G  104K  1.8G   1% /dev/shm
lrm                   1.8G  2.0M  1.8G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdf1             466G   32K  466G   1% /media/My Book_
.

---

### Post by taurus on 2009-02-03
> **/dev/sdf1 466G 32K 466G 1% /media/My Book_** 

/media/My Book_ is a mount point for /dev/sdf1 so you cannot remove it while it is still being used.  If you want to remove it, you first must unmount it (or /dev/sdf1).  Then, you can remove that directory.  

How do you mount /dev/sdf1, from /etc/fstab, by hand, or with automount?

---

### Post by metalmaniac248 on 2009-02-03
it mounts automatically when i log on

---

### Post by taurus on 2009-02-03
Post your /etc/fstab.

```
cat /etc/fstab
```

---

### Post by metalmaniac248 on 2009-02-03
> nick@nick-desktop:/media$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ecdf30c8-53a0-4c7b-8012-d289f0ded3e6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=458839d5-03eb-43a6-a178-77ecdf26888e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
.

---

### Post by taurus on 2009-02-03
Does /dev/sdf1 always plug in?  What happens if you unmount it and then plug it back in again, would it still mount /dev/sdf1 to /media/My Book_?

```
sudo unmount /dev/sdf1
```
Now unplug it and wait for 5 seconds and plug it back in.

```
df -h
```

---

### Post by metalmaniac248 on 2009-02-03
when i unmount it My Book_ disapears from the media folder buy My Book (which is the folder with all my stuff in) remains

---

### Post by taurus on 2009-02-03
While the drive is still unplugged, look and see if there is anything in /media/My Book.

```
ls -la /media/"My Book"
```

Otherwise, you could remove it if it's an empty directory.

```
sudo rmdir /media/"My Book"
ls -la /media
```

---

### Post by metalmaniac248 on 2009-02-03
no my files are still in the My Book directory its as iff the My Book directory is on my ubuntu filesysten

---

### Post by taurus on 2009-02-03
Maybe that's why /dev/sdf1 won't mount to /media/My Book since you already have stuff in there!

What if you rename /media/My Book to something else, then see if /dev/sdf1 would create a new one and mount to it?

---

### Post by metalmaniac248 on 2009-02-03
cant rename it

---

### Post by taurus on 2009-02-03
Can't as in don't want to or can't as in permission problem?

If the permission problem, what command did you run to rename it?

---

### Post by metalmaniac248 on 2009-02-03
the option is greyed out

---

### Post by taurus on 2009-02-03
Applications -> Accessories -> Terminal
```
sudo mv /media/"My Book" /media/MyBook
ls -la /media
```

---

### Post by metalmaniac248 on 2009-02-03
yer thanks problem solved now, somehow id managed to create a directory on my filesystem called My Book in the media directory, aand this was forcing my external HDD to mount its self at My Book_

---

### Post by taurus on 2009-02-03
> **metalmaniac248 said:**
> yer thanks problem solved now, somehow id managed to create a directory on my filesystem called My Book in the media directory, aand this was forcing my external HDD to mount its self at My Book_

Precisely.

---

