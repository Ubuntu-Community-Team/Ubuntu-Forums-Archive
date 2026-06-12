---
title: "HDD failed to mount"
date: 2009-04-29
forum: General Help
---

### Post by FallFromINFINITY on 2009-04-29
Okay, here's the deal.

I just booted up my computer, no errors, and I've found that one of my harddrives labeled as DATA is no longer mounting.

The exact error on attempted mount is this:

```
Cannot mount volume.
Unable to mount the volume 'DATA'.

Details:
mount_point cannot contain the following
characters: newline, G_DIR_SEPARATOR (usually /)
```


Shortly later, another error appears:

```
Unable to mount DATA
DBus error org.freedesktop.DBus.Error.NoReply: Did
not receive a reply. Possible causes include: the
remote application did not send a reply, the message
bus security policy blocked the reply, the reply timeout
expired, or the network connection was broken.
```

I don't know the cause, and not even the r-click menu works, because it attempts to mount.

---

### Post by FallFromINFINITY on 2009-04-29
Bump.
Still no answer and it's proving a real problem.

Perhaps this information will help:
A couple of days ago, I changed the mount point to attach as a folder in my home folder, /home/Rich/DATA/, so accessing that folder would in turn, access the HDD instead. It worked yesterday, but now is not mounting.

Would unplugging the hard drive, restarting the system, then restarting the system again with it plugged in register it under a new mount point?

---

### Post by taurus on 2009-04-29
What filesystem is that harddrive?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by FallFromINFINITY on 2009-04-29
FAT32 (was already formatted from my previous OS install)
shows up as vfat to linux

---

### Post by taurus on 2009-04-29
How did you mount it to $HOME/DATA?  It's not a good idea to mount vfat/ntfs filesystem to your $HOME.  Instead, mount it somewhere like /media/DATA or /mnt/DATA and create a link to that, i.e.

```
ln -s /media/DATA ~/DATA
```

---

### Post by FallFromINFINITY on 2009-04-29
How would I tell it where to mount?

The process I used was to right-click on the mounted drive, as it shows on the desktop, then under the "Drive" tab, set the mount point.

I do not know the terminal command to set the mount point.

---

### Post by taurus on 2009-04-29
If you want to have it mount automatically each time you boot Ubuntu, then you can edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add an entry at the end for it.  It should look something like, assuming it's /dev/sdb1.

```
/dev/sdb1   /media/DATA   vfat   iocharset=utf8,umask=000  0  0
```
Save it.  Then, create the new mount point and mount it.

```
sudo mkdir /media/DATA
sudo mount -a
df -h
```

---

### Post by FallFromINFINITY on 2009-04-29
Okay, thanks. That solved it.

Now another quick question, how would I have this automatically mount on boot to /media/DATA ?

---

### Post by taurus on 2009-04-29
If you add an entry for that drive in /etc/fstab, then it would be mounted automatically each time you boot Ubuntu.

Reboot and see what happens.

```
df -h
```

---

### Post by FallFromINFINITY on 2009-04-29
Cool. Thanks. The harddrive is now working correctly.

---

