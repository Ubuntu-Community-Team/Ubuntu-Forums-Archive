---
title: "Ubuntu not auto-mounting multisession CD"
date: 2009-03-06
forum: Desktop Environments
---

### Post by himuradenshin on 2009-03-06
Greetings,

I am experiencing an issue with multisession discs not auto-mounting in Ubuntu 8.10. The issue applies to open multisession discs (one, two or more sessions using "Continue multisession" in K3B's "Misc" tab) as well as closed multisession discs (using "Finish multisession" in K3B's "Misc" tab).


Context: This was tested on two seperate machines both running Intrepid Ibex with all updates installed as of March 6th 2009. Both machine's drives are known to work, Ubuntu mounting without problems Audio CDs and Data CDs/DVDs that are burned in DAO mode.


How to replicate (using K3b):

1- Insert blank cd in drive. Fire up K3B, add a file to project, choose "Start multisession" in the "Misc" tab (all other options untouched) and burn.

2- CD is ejected after successful burn. Close tray with CD still in and wait for media to be scanned.

/var/log/messages wields repeated entries like this one while the disc is being scanned:

```
Mar  6 13:28:25 ubuntu-desktop kernel: [51021.405035] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Mar  6 13:28:25 ubuntu-desktop kernel: [51021.405047] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Mar  6 13:28:25 ubuntu-desktop kernel: [51021.405053] sr 1:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
```

Normally, as with all other CD/DVD, an icon should appear on the desktop, the media being accessible via the "CD-RW/DVD-RW Drive" icon in nautilus' left navigation bar but nothing happens. Right-clicking on said nautilus' left nav bar icon and selecting "Rescan" wields no visible results.

Mounting manually with ```
sudo mount -a
``` wields no results.


Mounting manually with ```
mount /dev/scd0
``` or through K3B's "Device" menu successfully mounts the drive and a "cdrom0" icon appears on the desktop and a "cdrom0" icon appears in nautilus' left nav bar while the "CD-RW/DVD-RW Drive" icon remains visible although unusable.


Other config informations:

uname -a
```
Linux ubuntu-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
```

mount -V
```
mount from util-linux-ng 2.14 (with libvolume_id and selinux support)
```

k3b -v
```
Qt: 3.3.8b
KDE: 3.5.10
K3b: 1.0.5
```

fstab (edited for readability)
```
# /etc/fstab: static file system information.
#
# <file system>                           <mount point>   <type>       <options>                  <dump>  <pass>
proc                                      /proc           proc         defaults                   0       0
# /dev/sda5
UUID=f459ef51-7b0b-41e8-8f12-b9eb25baecad none            swap         sw                         0       0
# /dev/sda6
UUID=d8df48c9-1b4e-4341-acff-b38ddf159081 /               ext3         relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=9aee873b-28fa-49dd-9f2d-b919518c364a /home           ext3         relatime                   0       2
/dev/scd0                                 /media/cdrom0   udf,iso9660  user,noauto,exec,utf8      0       0
```



Thank you in advance for your insight and let me know if you need more troubleshooting informations!

---

### Post by himuradenshin on 2009-03-10
Anyone can replicate?

---

### Post by sciadellacometarossa on 2009-03-22
I can only say that I have the same issue.

I can mount multisession dvd with
sudo mount /dev/scd0

the result:
mount: block device /dev/scd0 is write-protected, mounting read-only

Then I can navigate directories but when I try to access file I get I/O errors.

---

### Post by himuradenshin on 2009-03-22
Thanks for confirming, Scia. I'm gonna open a bug on Ubuntu's launchpad if it is not fixed in Jaunty Jackalope to be released in april.

---

### Post by rfourie on 2009-03-26
All I can add is that I have exactly the same setup as himuradenshin and I have the same issues. I have tried everything including manually mounting and even restarting my X session (that worked once with one disc but not the others).
I'm trying to access some data backups I did ages ago, mostly on Windows machines, and this is quite a problem!

---

### Post by hyperair on 2012-01-04
For anyone who has stumbled upon this -- there's a bug open on this issue that you might want to subscribe yourself to: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/911810](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/911810)

---

