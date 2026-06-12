---
title: "permissions on external HD"
date: 2006-01-11
forum: General Help
---

### Post by gatorbrit on 2006-01-11
I use an external USB HD formatted FAT32.
Before I plug it in the mount point permissions are set as
```
drwxrwxrwx  2 root root  4096 2006-01-11 11:51 SEAGATE

```

Once I plug it in, these change to:
```
drwx------  22 richard richard 32768 1969-12-31 19:00 SEAGATE

```

How can I keep the permissions the same so I have full read -write access.
Thanks

---

### Post by lamego on 2006-01-11
You will need to remount it with the option umask=000 .

---

### Post by gatorbrit on 2006-01-11
OK, trouble is I don't actually mount the drive - I just plug it in the USB port and there it is.
So I can't set any options when I mount it.

---

### Post by gatorbrit on 2006-01-11
With the help above and referring to the gnome help, I figured it out and I want to post my solution so that anyone else can reference it and also because I will know where to look if I have the problem again!

**First.  The key is to prevent Ubuntu from automatically mounting the USB HD.**
System->Preferences->Removalable Drives and Media.
Uncheck the box that says "mount removable drives when hot plugged"

**Second. Find out the partition name of the external drive**
System->Administration->Disks
[B]
Third. Manually mount the drive[/B]

```
sudo mount /dev/sda1 /media/ext_hd/ -t vfat -o umask=000 

```

**Fourth to unmount **
```
sudo umount /media/ext_hd
```

The drive should be mounted with all permissions.

I tried editing the fstab file - but it caused problems on boot - maybe because the USB hot plug thing was not running - who knows.

---

