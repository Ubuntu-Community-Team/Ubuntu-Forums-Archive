---
title: "LiveUSB problem"
date: 2009-10-29
forum: Desktop Environments
---

### Post by bluegenie on 2009-10-29
I made an ISO image of Ubuntu9.04 LiveCD using MagicISO.
Then I made a LiveUSB off it using UNetbootin.
But when I run my system using this LiveUSB, I get this -

```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT ! does not exist. Dropping to a shall !

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```

Theres a syslinux.cfg file created by UNetbootin in my pendrive with following contents - 
```
default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label oem=OEM install (for manufacturers)
kernel /ubnkern
append initrd=/ubninit oem=oem-config/enable=true
```

I get these 3 options as seen above on startup.

---

