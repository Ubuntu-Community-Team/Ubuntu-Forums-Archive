---
title: "making img file from files within a directory with the dd command ?"
date: 2009-02-13
forum: General Help
---

### Post by andlinux on 2009-02-13
I have here a few directories with files in it and I want to make *.img files from the files that are standing in those directories.
I tried that with the dd command but it isn't working.

It's for virtualbox, the img files need to have the size of a floppy disk.

Who can help me ?

---

### Post by kanikilu on 2009-02-13
See if this helps: [http://ubuntuforums.org/showthread.php?t=484549](http://ubuntuforums.org/showthread.php?t=484549)

---

### Post by andlinux on 2009-02-14
> **kanikilu said:**
> See if this helps: [http://ubuntuforums.org/showthread.php?t=484549](http://ubuntuforums.org/showthread.php?t=484549)
Do you use that when you have a floppy drive ?

---

### Post by heindsight on 2009-02-14
It's much easier to do
```
mkdosfs -F 32 -C floppy.img 1440
sudo mount -o loop,uid=1000,gid=1000 floppy.img /mnt
```

change 1000 in uid=1000,gid=1000 to your uid/gid which you can obtain using the command: ```
id
```

Then copy all the files you want to put into floppy.img to /mnt. The uid=,gid= options to mount means that you'll have permission to do this as a normal user without using sudo.

Finally, unmount the image using
```
sudo umount /mnt
```

If you have a floppy drive and want to write the image to a floppy, just use
```
sudo dd if=floppy.img of=/dev/fd0 bs=512 count=2880
```

---

