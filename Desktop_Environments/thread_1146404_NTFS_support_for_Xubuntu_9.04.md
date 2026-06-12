---
title: "NTFS support for Xubuntu 9.04"
date: 2009-05-02
forum: Desktop Environments
---

### Post by Firidan on 2009-05-02
When I booted in Xubuntu live CD I noticed that it didn't mount my windows partition. How do I get Xubuntu to suport ntfs?:guitar:

---

### Post by taurus on 2009-05-02
Try mounting it by hand from a terminal.

```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda1 /media/windows
df -h
```
_Assuming_ /dev/sda1 is where windows is.

---

### Post by Firidan on 2009-05-02
I have partitions C and D plus Xubuntu. Does counting start at sd0 or sd1?
How do I make xubuntu to always mount windows patitions?

---

### Post by taurus on 2009-05-02
Just look at the output of this command.

```
sudo fdisk -l
```
That would be a lower case letter L, not number 1.

---

### Post by Firidan on 2009-05-03
Thanks, it works

---

### Post by freakyfrog on 2009-06-11
> **taurus said:**
> Try mounting it by hand from a terminal.

```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda1 /media/windows
df -h
```_Assuming_ /dev/sda1 is where windows is.

Thanks taurus, this works. But I want to automatically mount the NTFS partition on startup. Can you tell me how? I was under the impression that the latest ubuntu releases automatically detect and mount NTFS partitions on startup.

---

### Post by freakyfrog on 2009-06-11
Addition: I'm not using a live CD - I've installed xubuntu to my hard disk. I believe once you've installed, NTFS partitions should auto-mount?

---

### Post by PureLoneWolf on 2009-06-11
They don't auto-mount - Normally you see the device listed in your file manager and clicking it for the first time will mount it and place a volume icon on the desktop.  USB devices normally automount though.

For Ubuntu I used PYSDM (sudo apt-get install pysdm) to setup my fstab file (until I got used to it) - It is a GUI that shows your available disks and allows you to specify mount points, permissions etc..

Give it a try, it will get you up and running.

---

### Post by freakyfrog on 2009-06-11
I got [**PYSDM**]("http://pysdm.sourceforge.net/") and  it was a breeze. And when I restarted it did auto-mount, and that's what I wanted. Thanks, mate! :)

---

### Post by PureLoneWolf on 2009-06-11
Glad it helped you out :)

---

### Post by Ron O on 2009-08-02
Another grateful user! I finally got a handle on mounting partitions without fooling around with files like fstab. Thanks!

---

### Post by bagy on 2009-10-04
> **freakyfrog said:**
> Thanks taurus, this works. But I want to automatically mount the NTFS partition on startup. Can you tell me how? I was under the impression that the latest ubuntu releases automatically detect and mount NTFS partitions on startup.

Edit fstab file

```
sudo mousepad /etc/fstab
```

add line:
/dev/sda1   /media/name    auto

---

