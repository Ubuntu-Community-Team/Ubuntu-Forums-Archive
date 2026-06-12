---
title: "Change Permissions For FAT32 Slave Drive"
date: 2005-12-11
forum: Desktop Environments
---

### Post by mcescher on 2005-12-11
The problem I am having is that I want to write to a mounted FAT32 slave drive and it says I do not have permission.

I went to create a folder in a FAT32 drive today and it would not let me write to it from Linux. I checked permissions and I only have read only permission.

So I tried to log in as root and then navigate to the drive and change permissions by right clicking...slecting properties...and changing the owner of the drive and it would not allow it saying "The owner could not be changed."

Any ideas?

---

### Post by arnieboy on 2005-12-11
please paste the contents of the following command from terminal:
```
cat /etc/fstab
```

---

### Post by mcescher on 2005-12-11
Here ya go.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hdb5       /media/windows  vfat    iocharset=utf8,rw,user,exec,umask=000

---

### Post by aysiu on 2005-12-11
[QUOTE=mcescher]
/dev/hdb5       /media/windows  vfat    iocharset=utf8,rw,user,exec,umask=000[/QUOTE] This works for me: ```
/dev/hdb5  /media/windows  vfat  iocharset=utf8,umask=000   0  0
```

---

### Post by mcescher on 2005-12-11
Ok...further clarification on the problem.

I changed my fstab file to include the text provided by aisyu.

I still can't change the ownership of the drive even after a reboot.

There is one file on the drive that has a smaller lock icon on the folder. This is the only folder on the drive and the one that I wanted to add stuff to. I can't change the ownership of this file or the entire drive even when logged in as root.

When logged in as my usual username I can write to the drive itself...but not to the locked folder that is on the drive already.

---

### Post by mcescher on 2005-12-11
Ok this is wierd now.

I logged back in as my normal user and now I have the permissions to write to that folder.

The small lock icon is gone and I can open the folder and add files within it.

The wierd thing is that now...2 out of the 10 subfolders within this folder are now locked and I have read only permissions on them.

---

### Post by aysiu on 2005-12-11
So the drive is fine.
It's just that one file on the drive that's not fine.
I'm surprised even root can't touch it.

I don't know what to tell you.

---

### Post by mcescher on 2005-12-11
Well as long as I have access to the main folder on the drive I will be fine.

Thanks for the help!

---

### Post by arnieboy on 2005-12-11
This is what u are doing wrong.
you are mounting both your NTFS and FAT32 partitions in the same folder (/media/windows)
do the following:
```
sudo mkdir /media/fat32
sudo mkdir /media/ntfs
sudo gedit /etc/fstab
```
erase everything and make it look as follows:
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /media/ntfs ntfs nls=utf8,umask=0222 0 0
/dev/hdb5 /media/fat32 vfat iocharset=utf8,umask=000 0 0
save and exit and restart your computer.
now u will have your fat32 partition mounted on to /media/fat32
and your ntfs partition mounted on to /media/ntfs and u will read and write permissions on the former and only read permissions on the latter. No more locked files in the former.

---

### Post by aysiu on 2005-12-11
I didn't spot that, but you're totally on, Arnieboy! Eagle eyes!

---

### Post by arnieboy on 2005-12-11
edited my last post (fstab entry) a bit.. please read it again. Thanks aysiu.. now I gotta get back to wrapping up my own work.. lol...

---

### Post by mcescher on 2005-12-11
So I followed arnieboys advice and it left me in the same situation as my previous post.

I can now write to the FAT32 drive except for 2 subfolders which are locked. Previously I had both drives named "windows" and Ubuntu displayed them as "windows" and "windows (2)". Other than the confusing names it didn't really present much of a problem for me.

Thanks for the help in re-naming them though.

---

### Post by aysiu on 2005-12-11
So can you re-post what your revised /etc/fstab looks like now?

---

### Post by mcescher on 2005-12-12
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /media/ntfs ntfs nls=utf8,umask=0222 0 0
/dev/hdb5 /media/fat32 vfat iocharset=utf8,umask=000 0 0

---

### Post by aysiu on 2005-12-12
Looks good to me. And you tried rebooting, too?

---

### Post by mcescher on 2005-12-14
Yup...re-booted several times.

Don't get me wrong..this fix did solve my original issue...the only caveat was that I ended up with two subfolders being locked (not necessarily as a result of your help).

Not a big deal though and I appreciate all the help.

---

