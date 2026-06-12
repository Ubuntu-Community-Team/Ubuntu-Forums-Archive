---
title: "mounting VFat32, now I need permissions"
date: 2006-09-17
forum: Desktop Environments
---

### Post by yeehawjared on 2006-09-17
I have a partition called STORAGE that's FAT32.  

lrwxrwxrwx  1 root  root      6 2006-09-13 17:14 cdrom -> cdrom0
drwxr-xr-x  2 root  root   4096 2006-09-13 17:14 cdrom0
drwx------  3 jared jared 16384 1969-12-31 19:00 mmcdisk
drwxr-xr-x 12 root  root  32768 1969-12-31 19:00 STORAGE

I cannot create any folders in STORAGE.  It says:

jared@jaredtop:/media/STORAGE$ mkdir test
mkdir: cannot create directory `test': Permission denied

So it looks like root is the only one that can make folders there.  I try to change the owner from root to jared, but it doesn't work:

jared@jaredtop:/media$ chown jared -v -R /media/STORAGE/
I get an error on every file:
failed to change ownership of 'XXXXXXX'


one more thing, here's my /etc/fstab entry for this partition:

/dev/sda5	/media/STORAGE	vfat	defaults	1	0

so how do I make STORAGE so that jared can create directories?  Thanks guys :)

---

### Post by kuja on 2006-09-17
sudo chown -R jared:jared /media/STORAGE/

---

### Post by yeehawjared on 2006-09-17
still getting operation not permitted:

chown: changing ownership of `/media/STORAGE/randomfile': Operation not permitted

any thoughts? :confused:

---

### Post by Omnios on 2006-09-17
Came up with this about a year ago and have been using ever since.

```

/dev/hda2       /media/documents     vfat    rw,users,gid=users,umask=000,       0       0

```

---

### Post by kuja on 2006-09-17
Try taking off the -R

I almost forgot that it's a VFAT fs, meaning that none of the files have permissions.

Also, in place of defaults, try putting "uid=jared,gid=jared".

---

### Post by yeehawjared on 2006-09-17
/dev/hda2       /media/documents     vfat    rw,users,gid=users,umask=000,       0       0

worked like a charm!!!  thanks for all your help guys :)

---

