---
title: "Hibernate(s2disk) problem due to USB device?"
date: 2010-07-21
forum: Desktop Environments
---

### Post by leekyuh on 2010-07-21
Hello, I recently installed uswsusp on my Lucid(10.04) 32 bit system.
I have RAID0 configuration over 2 500GB HDD's, with windows and Ubuntu partitions.
The mainboard(Gigabyte GA-P55A-UD4 Intel P55) supports USB 3.0, but I don't use any 3.0 device.

When I run s2disk, the screen shows "s2disk: Snapshotting the system" and returns to Gnome environment immediately.

The swap partition is enabled.
```

# swapon -s
Filename                Type        Size    Used    Priority
/dev/mapper/isw_ccidhjihgj_Seagate5     partition    15623172    84    -1

```Here's the kernel log file(/var/log/kern.log) which shows the error.
```

Jul 21 11:36:07 leeq-lab kernel: [ 3435.491889] PM: Marking nosave pages: 0000000000002000 - 0000000000006000
Jul 21 11:36:07 leeq-lab kernel: [ 3435.491895] PM: Marking nosave pages: 0000000000094000 - 0000000000100000
Jul 21 11:36:07 leeq-lab kernel: [ 3435.491900] PM: Basic memory bitmaps created
Jul 21 11:36:09 leeq-lab kernel: [ 3436.630156] Syncing filesystems ... done.
Jul 21 11:36:09 leeq-lab kernel: [ 3436.882111] Freezing user space processes ... (elapsed 0.00 seconds) done.
Jul 21 11:36:09 leeq-lab kernel: [ 3436.883002] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Jul 21 11:36:09 leeq-lab kernel: [ 3436.883405] PM: Preallocating image memory... done (allocated 472001 pages)
Jul 21 11:36:09 leeq-lab kernel: [ 3437.109925] PM: Allocated 1888004 kbytes in 0.22 seconds (8581.83 MB/s)
Jul 21 11:36:09 leeq-lab kernel: [ 3437.109926] Suspending console(s) (use no_console_suspend to debug)
Jul 21 11:36:09 leeq-lab kernel: [ 3437.110213] pm_op(): usb_dev_freeze+0x0/0x20 returns -2
Jul 21 11:36:09 leeq-lab kernel: [ 3437.110214] PM: Device usb10 failed to freeze: error -2
Jul 21 11:36:09 leeq-lab kernel: [ 3437.171543] PM: restore of devices complete after 1.257 msecs
Jul 21 11:36:09 leeq-lab kernel: [ 3437.448768] Restarting tasks ... done.
Jul 21 11:36:09 leeq-lab kernel: [ 3437.474240] PM: Basic memory bitmaps freed

```And lsusb:
```

# lsusb
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 009: ID 05ac:1294 Apple, Inc. iPhone 3GS
Bus 001 Device 008: ID 046d:c068 Logitech, Inc. 
Bus 001 Device 007: ID 046a:0021 Cherry GmbH 
Bus 001 Device 006: ID 050d:0307 Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I tried removing all the USB devices except my Cherry keyboard, but no luck.
I suspect it's something to do with USB 3.0, which may not yet supported well by kernel?
Any ideas?

Thanks.

---

### Post by gc2712 on 2010-10-24
I too have had exactly the same problem with a Gigabyte H57 motherboard with USB 3. I too do not use any USB 3.0 devices yet. The symptoms are that the system wakes immediately after suspend and returns to login screen. As suspend to ram is very important to me in terms of power saving any help greatly appreciated.
Dmesg:
 [ 1083.659188] pm_op(): usb_dev_suspend+0x0/0x20 returns -2 [ 1083.659192] 
PM: Device usb10 failed to suspend: error -2 [ 1083.659194] 
PM: Some devices failed to suspend 
   
lsusb: 
  Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 005: ID 0a81:0101 Chesen Electronics Corp. Keyboard 
Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical 
Bus 001 Device 003: ID 046d:08c5 Logitech, Inc. QuickCam Pro 5000 
Bus 001 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

As a follow up to this post, I later tried disabling the USB 3.0 controller in BIOS and lo! suspend to ram (sleep) worked!! Re-enabling the USB 3.0 controller recreated the original symptoms of appearing to suspend, but then "waking" immediately. So there appears to be a bug or problem for Linux Mint  (Lucid) suspending USB 3.) controller. At leats on this Gigabyte H57M-USB3 motherboard.

---

### Post by griamdu on 2010-11-05
Same problem with my mainboard ASUS M4A89GTD PRO USB3 on Ubuntu 10.10 (I do not use uswsusp instead, but included default packages). 

Both suspend and hibernate tasks fail unless I disable USB 3 support in BIOS settings.


In addition : this is the referenced bug for the xhci module (eXtended Host Controller) that control the USB 3 interface
[URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998"]
https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998[/URL]

---

### Post by nightfrost on 2010-11-09
Glad I found this thread. I have the exact same problem. I'll keep an eye on this thread for a solution, or post mine if I find one :)

---

### Post by leonbravo on 2011-03-17
you may try the solution suggested in [http://jr0cket.blogspot.com/2010/10/ubuntu-1010-hibernate-suspend-bug-fix.html?showComment=1300390993852#c3567939023077361774](http://jr0cket.blogspot.com/2010/10/ubuntu-1010-hibernate-suspend-bug-fix.html?showComment=1300390993852#c3567939023077361774)

it's the same bug description posted previously. However, be aware the file to edit can be changed to /etc/pm/config.d/unload_modules (with s at the end.)

---

### Post by gc2712 on 2011-04-04
> **leonbravo said:**
> you may try the solution suggested in [http://jr0cket.blogspot.com/2010/10/ubuntu-1010-hibernate-suspend-bug-fix.html?showComment=1300390993852#c3567939023077361774](http://jr0cket.blogspot.com/2010/10/ubuntu-1010-hibernate-suspend-bug-fix.html?showComment=1300390993852#c3567939023077361774)

it's the same bug description posted previously. However, be aware the file to edit can be changed to /etc/pm/config.d/unload_modules (with s at the end.)

Thanks for this solution it worked for me with a Gigabyte H57MUSB3 motherboard. It would not suspend whether any device plugged in to usb3 or not. Now with this solution it does. :)

---

