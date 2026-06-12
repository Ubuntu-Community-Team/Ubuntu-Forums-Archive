---
title: "Can't write to USB ext hard drive"
date: 2006-02-12
forum: Desktop Environments
---

### Post by whitetr6 on 2006-02-12
I have an external usb drive that I used to back up my system when I moved to Ubuntu. I can read from it no problem, but if I try to write to it, everything is read only. In looking at the permissions, it says I can't change the permissions because I am not the owner. How do I fix that?

Thanks!

---

### Post by Ramses de Norre on 2006-02-12
Who is the owner? You can change it with ```
sudo chown 'your username' 'file name'
```

You say you used it to back up before moving to ubuntu? Is it ntfs then? In that case you simply can't write on it. (theoretically you can but I wouldn't recommend to)

---

### Post by whitetr6 on 2006-02-12
I tried that, and it appeared to be working, but it still says the same thing. It's like the whole disk is read only.

I ran mount, and it shows up as:
/dev/sdd1 on /media/New Volume type ntfs (rw,noexec,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8)

Is the problem that it is type ntfs?

---

### Post by Ramses de Norre on 2006-02-12
Yes, you can't write on ntfs. Has to do with ntfs being developed by microsoft.
Only thing you can do if you want to be able to write on the disc is back up the data and repartion it..

---

### Post by spin2cool on 2006-02-12
For maximum flexibility, keep your data on FAT partitions.  They're readable and writeable by all major OSes.

---

### Post by whitetr6 on 2006-02-12
OK, cool. Thanks guys

---

### Post by brian g on 2006-02-16
i have a similar problem with my thumb drive
i pop in my usb drive and it auto mounts as expected but i can't write anything to it

mount yields the following
/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)

the drives permissions tab tells me that I am the owner
but at the bottom of the same tab it says I am not the owner.

---

### Post by jj-johjoh on 2008-05-14
I'm having the same problem.

I've already installed ntfs-config, it enables me to write on my internal NTFS HD, but not in the external...

Also I've made a partition on my external USB HD using the EXT3 file system (with PartitionMagic 8), hoping that then I'd be able to store files on it, but had no success...

[-o<

DAAAAAAAAMN! I just don't know what to doooo!
I need to backup my Windows files, WITHOUT USING WINDOWS!!! (it simply crashed...)

If anyone could help, I'd be glad.

---

