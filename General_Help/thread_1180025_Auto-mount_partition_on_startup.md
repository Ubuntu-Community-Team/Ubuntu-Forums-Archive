---
title: "Auto-mount partition on startup?"
date: 2009-06-06
forum: General Help
---

### Post by yonyz on 2009-06-06
How can I set an NTFS partition to automatically mount when Ubuntu starts?

---

### Post by Bucky Ball on 2009-06-06
Go to Synaptic Package Manager, search for and install:

ntfs-3g

Run it and that will set up your ntfs partitions in your fstab for you. :)

It can, of course, be done manually, but this is quick and easy.

---

### Post by tad1073 on 2009-06-06
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by yonyz on 2009-06-07
Bucky Ball: How do I run ntfs-3g?
tad1073: I can't find anything about AUTO mounting in this article:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by Bucky Ball on 2009-06-07
System->Administration->Synaptic Package Manager

Then do a search for:

ntfs-3g

Once installed, you will find it in one of the drop down menus in the toolbar (sorry can't be more specific, not running it on this machine). Run it, it will identify your ntfs drive and ask if you want to change your fstab file to mount them at boot. :)

---

### Post by DeMus on 2009-06-07
> **yonyz said:**
> How can I set an NTFS partition to automatically mount when Ubuntu starts?

_Auto mount Windows disks_
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have [COLOR="Red"]NO[/COLOR] drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

---

### Post by Bucky Ball on 2009-06-07
As explained by DeMus ... nice one. :)

---

### Post by yonyz on 2009-06-07
Thank you very much!

---

### Post by keypox on 2009-06-16
> **DeMus said:**
> _Auto mount Windows disks_
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have [COLOR="Red"]NO[/COLOR] drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.


Thank you so much this should be sticky ;)

---

### Post by texla on 2011-03-28
Yep, good one!

---

