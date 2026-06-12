---
title: "Permission and Mounting problems"
date: 2008-06-23
forum: Debian
---

### Post by kk0sse54 on 2008-06-23
So I've had Debian Lenny installed just recently on my desktop and so far I am really liking it. I have only come across one problem though, which is that I cannot mount my other partitions on my computer. I had this same problem with an external hard drive too and every time I tried to mount anything it always said permission denied. So I thought nothing of it and went about changing the ownership and such and I got my External HD to work but I couldn't get the other partitions to work. I then tried to open nautilus with root privileges and tried to mount the partitions from there only to get:
Error org.freedesktop.DBus.Error.AccessDenied
Details>
    A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.HAL.Device.Volume" member "Mount" error name "(unset)" destination "org.freedesktop.HSL")

I am quite stumped as to what to do next. The information on the partitions I am trying to mount are:
1. ntfs /dev/sda2 /media/disk
2. ext3 /dev/sda5 /media/disk-0
3. ext3 /dev/sda8 /media/disk-1
and the external is even though I got it to work: ntfs /dev/sdb1 /media/OneTouch4

If anybody could help with this problem I would greatly appreciate it as it's really the only thing holding me back from using Debian as my main OS.

---

### Post by tturrisi on 2008-06-25
as root:
apt-get install build-essential linux-headers-`uname -r`
cs /usr/src
wget [http://www.ntfs-3g.org/ntfs-3g-1.2531.tgz](http://www.ntfs-3g.org/ntfs-3g-1.2531.tgz)
tar xvfz ntfs-3g-1.2531.tgz
cd ntfs3g-1.2531
./configure
make
make install

to mount ntfs partitions at boot:
editor /etc/fstab
add the following line(s) for each partition where dirNAME = name you want for mounted partition:
(use tab key, not spacebar key)
/dev/sda1 /mnt/dirNAME ntfs-3g defaults 0 0
(and as root, you must also create the dirNAME in /mnt)

---

### Post by robb0100 on 2008-07-05
Thanks for the post tturrisi.

Is ntfs-3g-1.2531 a recommended patch for Hardy to allow ntfs partitions to be mounted using NFS? I believe there is an issue with sharing an ntfs partition using NFS.
Presumably there is a reason for it not being included in the current updates.

---

### Post by tturrisi on 2008-07-05
> **robb0100 said:**
> Thanks for the post tturrisi.

Is ntfs-3g-1.2531 a recommended patch for Hardy to allow ntfs partitions to be mounted using NFS? I believe there is an issue with sharing an ntfs partition using NFS.
Presumably there is a reason for it not being included in the current updates.

I don't know, I don't use ubuntu, I use debian.

---

