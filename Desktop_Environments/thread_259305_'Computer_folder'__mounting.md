---
title: "'Computer folder' / mounting"
date: 2006-09-17
forum: Desktop Environments
---

### Post by grilkip on 2006-09-17
To access my two windows partitions I have added these lines to /etc/fstab:
```
/dev/hda1    /media/win1 	ntfs  nls=utf8,umask=0222 0    0
/dev/hda2    /media/win2 	ntfs  nls=utf8,umask=0222 0    0
```

This worked fine as it always has and after rebooting two new entries appeared in the 'Computer' folder. All exactly how it ussually goes.

But I wanted to try out write access, so I installed the apropriate packages and replaced those lines with:```
/dev/hda1    /media/win1 	ntfs-fuse    auto,gid=1001,umask=0002    0    0
/dev/hda2    /media/win2 	ntfs-fuse    auto,gid=1001,umask=0002    0    0
```The next time I went to my Computer folder and clicked one of the links, I got the following error: ```
**Unable to mount the selected volume.**
mount: according to mtab, /dev/hda2 is already mounted on /media/win2

mount failed
```I'd like to have this fixed, either that or a way to remove those links from the Computer folder.

anyone?

---

### Post by bernied on 2006-09-17
As the message says, the two partitions were already mounted, so you need to unmount them, then remount them.
Try this:
```
sudo umount /media/win{1,2}
sudo mount -a
```
Or, if that fails, reboot ubuntu.

---

### Post by bernied on 2006-09-17
But be very careful of writing to ntfs filesystems from linux - not well tested, so you'd better be backed up or you risk losing your windows install. Better to avoid completely.

---

### Post by grilkip on 2006-09-17
thanks.

I did try that, it doesn't help. When I mount them (using fstab) readonly it works as normal, when I use the readwrite lines it doesn't. Even when rebooting and all that.

I can live with readonly, but I don't see why it doesn't work.

And I did know that ntfs write is still experimental, I was only going to use it on my seperate documents/media partition. But thanks for the heads up!

Does anyone know how autocreating of links work? And more importantly: where I could modify it to create some desktop launchers for example?

---

