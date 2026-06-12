---
title: "gnome is not able to mount usb drives"
date: 2009-04-11
forum: General Help
---

### Post by fuser312 on 2009-04-11
i don't remember when or how it started but now my gnome is unable to mount usb drives. i have to switch to other user with kde, which mounts that drive successfully and i can use that drive now in my previous user account with gnome.  any suggestions to fix this.


P.S.  as you are at it, nautilus is now unable to open places > computer, it says it can't handle this type of locations

---

### Post by neu2buntu on 2009-04-11
maybe check your "user privileges" in >system>administration>users and groups and make sure "access external storage devices automatically" is ticked on

or maybe open terminal and do code ```
gconf-editor
``` and goto >apps>nautilus>preferences> and tick on "media_automount" and "media_automount_open"

---

### Post by fuser312 on 2009-04-11
thanx but they were already ticked, still stucked

---

### Post by neu2buntu on 2009-04-11
hmmm "!!! look at >system>preferences>sessions>startup programs>see if volume manager is ticked.. if not tick on and then reboot

---

### Post by fuser312 on 2009-04-11
still stucked buddy, it was marked too

---

### Post by Dejavou42 on 2009-04-11
what is the output of "lsusb"?

---

### Post by fuser312 on 2009-04-12
> Bus 007 Device 005: ID 0951:1607 Kingston Technology Data Traveler 2.0
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 05c6:6000 Qualcomm, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


seems no problem here

---

### Post by Dejavou42 on 2009-04-12
I'm going to go out on a limb here, but a while back I had a problem where usb drives would not mount. I had to disable ehci_hcd to get them to work. This will disable USB 2.0, but it may get your usb drives mounted again. 

Try:
```

sudo modprobe -r ehci_hcd

```

If that works, then go to the thread below, and follow the steps to permanently disable ehci_hcd.

[http://ubuntuforums.org/showthread.php?t=901895](http://ubuntuforums.org/showthread.php?t=901895)

On the upside, recently I re-enabled ehci_hcd just to see if it had been fixed in an update. It has worked again for about 2 weeks now.

Let me know if this solution doesn't work.


Also, include a dmesg output just after you connect a usb drive... That is how I caught the problem with ehci_hcd...

---

