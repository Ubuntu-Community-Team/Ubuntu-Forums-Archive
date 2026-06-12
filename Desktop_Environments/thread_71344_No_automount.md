---
title: "No automount?"
date: 2005-10-03
forum: Desktop Environments
---

### Post by Zalbor on 2005-10-03
Hello

I don't know why, but automount seems to have stopped working... If for example I put a CD in, it would mount it and put the icon on the desktop. Now I have to give the console command or double-click on it in "Computer".
But the big problem is with the usb stick, which isn't mounted automatically either and I don't know how to mount, so I can't access the files on it.

Any ideas please?

My user privileges in system>administration>users are all checked, and so are the mount options in system>preferences>removable media.

---

### Post by firecat53 on 2005-10-03
This happens to me sometimes, too, after a suspend/hibernate. I don't know how to FIX it yet, but to work around it, try
```
sudo /etc/init.d/hotplug restart
```
good luck!
Scott

---

### Post by Zalbor on 2005-10-04
No, that didn't fix it...
I think this problem appeared after I did [this](http://ubuntuforums.org/showthread.php?t=64583).

---

### Post by KingBahamut on 2005-10-04
well you can install usbview for status purposes....but im curious how the user issues could have caused what your experiencing. Have you considered a reinstallation?

---

### Post by Zalbor on 2005-10-04
I have, but that would mean erasing all installed packages (thankfully /home is on a different partition) and with the things happening with backports lately, I'm afraid I won't be able to find them again.

I'll check usbview, thanks...

---

### Post by Zalbor on 2005-10-05
Sorry again... How do I manually mount a usb flash drive?

---

### Post by firecat53 on 2005-10-05
1. Plug in the USB drive.
2. If you don't already know the drive designator, type ```
sudo cat /proc/partitions
``` If the drive is being recognized, you should see the various partitions for your hard drive, CD and the usb drive something like sda, sda1, uba1, etc. Hard drives are usually hda, hdb. My USB drives are sda or sdb.

3. Create a directory in /media or /mnt. /media is where the automounter puts it (/media/usbdisk).  ```
mkdir /media/usbdisk
```

4. ```
sudo mount -o rw /dev/sda1 /media/usbdisk
```  The filesystem type should be automatically recognized. Replace sda1 with the proper designator for your drive and /media/usbdisk with the directory you created.
Don't forget ubuntuguide.org and your friend Google!  There's a lot of info out there.
Good luck!
Scott

---

### Post by Zalbor on 2005-10-06
I have the guide, but I didn't see any part about mounting flash drives on it. And I didn't really know what kind of /dev file one is.
But the above worked, thanks.

---

### Post by ratfish on 2005-10-15
I'm having this same issue.  I have to mount cd's and memory keys manually. Did you have any luck?

---

### Post by jdtanner on 2005-10-16
There is a bugzilla for this...

[http://bugzilla.ubuntu.com/show_bug.cgi?id=17607](http://bugzilla.ubuntu.com/show_bug.cgi?id=17607)

It is a bit of a pain in the backside ;-)

Cheers,
JohnT

---

