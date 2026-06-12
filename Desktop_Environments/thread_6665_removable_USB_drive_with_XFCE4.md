---
title: "removable USB drive with XFCE4"
date: 2004-11-30
forum: Desktop Environments
---

### Post by benjou on 2004-11-30
Hello,

I am a real beginner in linux and thank god I could configure Ubuntu on my laptop without too much pain.
As my laptop is old (64Mb RAM) I sat up and use Xfce4 instead of GNOME.

Now I have this problem: while Gnome was recognizing and mounting every uSB or PCMCIA mass storage deviced I hot-plugged (and even giving me a nice desktop icon)
Xfce4 does not (nothing under /media exept floppy and cdrom)

but if I do "sudo cfdisk /dev/sda" then the partitionner is able to "see" the memorykey

1. What do I have to do to access my device?

2. What can I do to have it recognized automatically?

 ](*,)

---

### Post by HungSquirrel on 2004-11-30
1. If it doesn't already exist, make a mount point (you can make the mount point whatever you want; this is an example):
```
sudo mkdir /media/sda1
sudo gedit /etc/fstab
```

In that file, add a line similar to this, assuming your usb drive is /dev/sda and only has one partition:

```
/dev/sda1       /media/sda1     auto    rw,user  	0       0
```

Then, you can mount the drive with *mount /media/sda1*.

2. I don't know.  :/

---

### Post by benjou on 2004-12-01
Yes it works! Thanks! :-)

Until I can find a way to have it automatically, I'll just configure a few buttons for mounting and unmounting devices...

---

