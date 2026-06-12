---
title: "Accessing NTFS Swap?"
date: 2006-08-27
forum: Desktop Environments
---

### Post by kshymkiw on 2006-08-27
Hello all,

I am running the x64 version of Ubuntu 6.06.  I have 2 250GB HDD's in my PC.

I used 1 hard disk for the boot partition and Swap.

The second Hard Disk has all my media on it from when i was on Windows.  I am trying to mount and view that Hard Disk.

My fstab has this line on the end of it:

```
/dev/sdb1 /mnt/D ntfs users,owner,ro,umask=000 0 0
```

If i am in Terminal and do:
$ sudo cd /mnt/D
I can access the Directory.  If i use the File Browser, and i Navigate to /mnt and try to go into /mnt/D I get the following error:

```
You do not have the permissions necessary to view the contents of "D".
```

Any help on what i can do?

Thank you in advance for helping a semi newbie with this.

---

### Post by kshymkiw on 2006-08-27
Well I guess I figured this out.  I added:

```
gksudo gedit /usr/share/applications/Nautilus-root.desktop
```

Then in that file added:

```
[Desktop Entry]
Name=File Browser (Root)
Comment=Browse the filesystem with the file manager
Exec=gksudo "nautilus --browser %U"
Icon=file-manager
Terminal=false
Type=Application
Categories=Application;System;
```

Now I have a root access File Browser

---

### Post by simonn on 2006-08-27
> **kshymkiw said:**
> Now I have a root access File Browser

Excellent, instead of trying to solve the root of the problem you can now delete all the files on the system accidentally

What you need to do is use something like the following in /etc/fstab:

```
/dev/sdb1 /mnt/D ntfs ro,uid=USER,gid=GROUP,umask=007 0 0
```

Replace USER with the user on your system you want to give ownership to.

Replace GROUP with the group on your system who's members you want to allow access to the files.

ro is a bit redundant, but probably good to spell out your intentions.

umask 007 means that only members of GROUP and USER will have access to the files.

See the NTFS options in man mount for more information.

---

### Post by kshymkiw on 2006-08-27
> Replace USER with the user on your system you want to give ownership to.

Replace GROUP with the group on your system who's members you want to allow access to the files.

ro is a bit redundant, but probably good to spell out your intentions.

umask 007 means that only members of GROUP and USER will have access to the files.

See the NTFS options in man mount for more information.

Ok i did that.  Now I have this:

```
/dev/sdb1 /mnt/D ntfs ro,kevin,users,umask=007 0 0
```

also tried this:

```
/dev/sdb1 /mnt/D ntfs ro,uid=kevin,gid=users,umask=007 0 0
```

and this:

```
/dev/sdb1 /mnt/D ntfs ro,uid=1000,gid=100,umask=007 0 0
```

And I am still getting the same error as before.

---

### Post by simonn on 2006-08-27
> **kshymkiw said:**
> Ok i did that.

No you didn't. Slow down and read it again.

/dev/sdb1 /mnt/D ntfs ro,**uid=**kevin,**gid=**users,umask=007 0 0

EDIT: just seen your edit and you have tried the above.

---

### Post by simonn on 2006-08-27
What does the following return when you have mounted the drive?

> 
$ ls -ld /mnt/D


---

### Post by kshymkiw on 2006-08-27
yea i have been editing my post there.  Should i take out uid and gid? and just use the equivelenat number/name?

---

### Post by kshymkiw on 2006-08-27
> **simonn said:**
> What does the following return when you have mounted the drive?

I get:

kevin@ubuntu-x64:~$ ls -ld /mnt/D
d--------- 1 root root 8192 2006-08-22 08:31 /mnt/D
kevin@ubuntu-x64:~$

---

### Post by simonn on 2006-08-27
Weird.

Yes, try numbers for uid and gid.

---

### Post by kshymkiw on 2006-08-27
still getting the same error.  I now have

```
/dev/sdb1 /mnt/D ntfs ro,uid=1000,gid=100,umask=007 0 0
```

---

### Post by simonn on 2006-08-27
Weird.

Try taking out the ro.

---

### Post by kshymkiw on 2006-08-27
> **simonn said:**
> Weird.

Try taking out the ro.

Alright

```
/dev/sdb1 /mnt/D ntfs uid=1000,gid=100,umask=007 0 0
```

Same Error

---

### Post by simonn on 2006-08-27
What command are you using to mount everything?

---

### Post by kshymkiw on 2006-08-27
> **simonn said:**
> What command are you using to mount everything?

mount -a

---

### Post by kshymkiw on 2006-08-27
> **simonn said:**
> What command are you using to mount everything?
also tried

```
root@ubuntu-x64:/home/kevin# mount /dev/sdb1
```

and got:

```
mount: /dev/sdb1 already mounted or /mnt/D busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt/D
```

---

### Post by simonn on 2006-08-27
You need to umount a drive before mounting it again.

Make sure nothing is using anything under /mnt/D - if something is then you will get the  busy error - and:

```

$ sudo umount /dev/sdb1

```

Edit /etc/fstab:

```

/dev/sdb1 /mnt/D ntfs ro,uid=kevin,gid=users,umask=007 0 0

```

Then:

```

$ sudo mount /dev/sdb1

```

---

### Post by kshymkiw on 2006-08-29
Tried in this order:

```
root@ubuntu-x64:/home/kevin# umount /dev/sdb1
root@ubuntu-x64:/home/kevin# vi /etc/fstab
root@ubuntu-x64:/home/kevin# mount /dev/sdb1
root@ubuntu-x64:/home/kevin# ls -ld /mnt/D
d--------- 1 root root 8192 2006-08-22 08:31 /mnt/D
```

/etc/fstab looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1 /mnt/D ntfs ro,uid=kevin,gid=users,umask=007 0 0
```

Still not working

---

### Post by simonn on 2006-08-29
what does the following return?

```

$ find /lib/modules -name *ntfs*

```

---

