---
title: "Breezy server mkisofs on ntfs"
date: 2009-05-24
forum: General Help
---

### Post by daddysmonsters on 2009-05-24
So I have a breezy server running. I am connected via ssh and have created a dir for my mount and ran

```
mount -t ntfs /dev/hdc1 /location/of/mount
```I can now access my ntfs drive and I used apt to install cdrecord and mkisofs. However I've hit a snag, the files system was mounted as read only and I need to create an iso or two and burn some files to disc via cdrecord. I was advised to use ntfs-3g however this comes up as an invalid option. Any light that could be shed would be wonderful.

---

### Post by nandemonai on 2009-05-24
> **daddysmonsters said:**
> So I have a breezy server running. I am connected via ssh and have created a dir for my mount and ran

```
mount -t ntfs /dev/hdc1 /location/of/mount
```I can now access my ntfs drive and I used apt to install cdrecord and mkisofs. However I've hit a snag, the files system was mounted as read only and I need to create an iso or two and burn some files to disc via cdrecord. I was advised to use ntfs-3g however this comes up as an invalid option. Any light that could be shed would be wonderful.

Have you got ntfs-3g installed? (Not sure on Breezy support).

---

### Post by daddysmonsters on 2009-05-24
Apparently not, I've tried an apt-get install ntfs-3g no love though. Anyone aware of the package name or if it is available in a repo for breezy? I don't imagine support would be an issue, although it may very well not be available in a deb for breezy. Just don't want to tamper with my server my network is mostly 9.04 but breezy has served me quite well (no pun intended) :D

EDIT: Scratch that, I just wget the 9.04 and will upgrade no harm in setting up a ssh server again. Thanks for the help though guys. :)

---

