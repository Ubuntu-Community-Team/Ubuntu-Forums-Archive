---
title: "xfce automount work, but mount as root not as user"
date: 2012-07-08
forum: Desktop Environments
---

### Post by h113331pp on 2012-07-08
Hi, I think I need some help.

I use slim and xfce4 on my ubuntu10.04, and my problem is that xfce automount the usb drive as root, so I can open it with thunar, but can`t write to it.

I also tried this command to mount:

exo-mount  -h  my_usb_udi

but it still mounted as root :(

I would be appreciated with any idea.

---

### Post by ronnysingh on 2012-07-09
The same thing happened with my Transcrend external HDD which I could access only by mounting it by using 'storage device manager'. I was able to read the disk but was not able to change its properties as the properties window mentioned that root is the owner and I can't the permissions because I was not the owner.

---

### Post by h113331pp on 2012-07-09
I copy /etc/xdg/xfce4/mount.rc from Xubuntu live cd to my system`s /etc/xdg/xfce4/ directory, and the problem solved.

So it need the rc file to let xfce know which uid should mount the usb flash drive.

---

