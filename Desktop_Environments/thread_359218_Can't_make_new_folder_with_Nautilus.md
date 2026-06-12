---
title: "Can't make new folder with Nautilus"
date: 2007-02-11
forum: Desktop Environments
---

### Post by dbarbour on 2007-02-11
Added a new HDD to my box. Added a line to fstab to mount the thing automatically.

```
/dev/sda5   /media/storage    ext2    defaults,user    0    2
```
I then changed the permissions and ownership as follows:

```
sudo chown dbarbour:dbarbour /media/storage
sudo chmod 755 /media/storage
```

Open Nautilus, browse to the directory, right-click. The "Create Folder" and "Create Document" options are grayed out. What am I missing?

(and yeah... ext2 v. ext3... I'll fix that later. :) )

---

### Post by taurus on 2007-02-11
Output of these.

```
id
ls -la /media
```

---

### Post by shareMenaPeace on 2007-02-11
Not sure but isnt the command

```
sudo chown dbarbour /media/storage
```

---

### Post by dbarbour on 2007-02-11
```
dbarbour@dbarbour-laptop:~$ id
uid=1000(dbarbour) gid=1000(dbarbour) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin),1000(dbarbour)
dbarbour@dbarbour-laptop:~$ ls -la /media
total 24
drwxr-xr-x  6 root     root     4096 2007-02-10 21:05 .
drwxr-xr-x 21 root     root     4096 2007-02-11 16:37 ..
lrwxrwxrwx  1 root     root        6 2007-02-01 12:24 cdrom -> cdrom0
drwxr-xr-x  2 root     root     4096 2007-02-01 12:24 cdrom0
drwxr-xr-x  2 root     root     4096 2007-02-01 12:24 sda1
drwxr-xr-x 31 dbarbour dbarbour 4096 2007-02-11 15:48 storage
drwxr-xr-x  2 root     root     4096 2007-02-05 23:10 USB

```

As for the format of the chown command, using username:username also changes the group.

---

### Post by taurus on 2007-02-11
I would remove the user option from the entry for /dev/sda5 in /etc/fstab.

```
/dev/sda5   /media/storage    ext2    defaults    0    2
```

---

### Post by dbarbour on 2007-02-12
Changing the permissions seems to have worked... after a reboot. Seems I just needed to restart that program. Thanks, though!

---

