---
title: "[SOLVED] SD/MMC card 1420N not working"
date: 2008-02-16
forum: Dell  Ubuntu Support
---

### Post by projektdotnet on 2008-02-16
I have a dell Inspiron 1420N with an SD/MMC slot but it does not work. Here's the output of lspci -nn and lsusb

```
$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

```

```
$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c510 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 006: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 005: ID 413c:8126 Dell Computer Corp. 
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  

```

The logitec is a wireless mouse so ignore it.

Also when I insert an SD card into the slot there is no output in dmesg.

Any ideas?
Thanks

---

### Post by th3t1nm4n on 2008-02-27
I'm having the same problem. *bump*

---

### Post by Mordac85 on 2008-02-27
If nothing is coming up in dmesg when you insert a card, do you have the sdhci module loaded?  Check w/modprobe and if it's there you may have to manually mount it.  It's named oddly but ls /dev/mmc* should do the trick.

---

### Post by fragos on 2008-02-27
The 1420n, like many laptops, doesn't use USB for the card reader. I purchased a 1420n with 7.04 and have upgraded to 7.10 using the Dell 7.10 DVD.  In both instances the card reader worked perfectly. If one installed a regular Ubuntu 7.10 live CD there's a good chance the card reader won't work.

---

### Post by provisional_idiot on 2008-02-28
so i have a dell inspiron 1420 as well, but my sd/mmc  seems to be working just fine.... 

mtab entry:
/dev/mmcblk0p1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0

mount output:
/dev/mmcblk0p1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

if anyone wants more info about  a particular file let me know

---

### Post by Mordac85 on 2008-02-28
Yep, my D430 just needed me to load the module and mount it.

---

### Post by projektdotnet on 2008-03-09
Ok so apparently I'm a little stupid. I was on the phone with Dell's Ubuntu support line and after a quick LSPCI and checking his Bios Simulator he asked me to check to see if the hardware was enabled in the BIOS and sure enough...it wasn't. As soon as I toggled the Media Card/1394 back on (Bios -> onboard devices) and reboot it worked perfectly with no further config needed.

---

### Post by lrich28 on 2008-03-11
How is the dell iso different from the normal one?

---

### Post by fragos on 2008-03-11
There difference are small but important to ensure the system works out of the box.  In some instances drivers and in other configuration files.  I even noticed a tab for touchpad in the mouse preference that isn't in the Ubuntu release.  I've heard there is a bundled license for a DVD ap that plays commercial DVDs that use DVDCSS scrambling.  Check out [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10).

---

### Post by fuwkej on 2008-03-20
Could anyone post the dummy version of how to mount the xD card? I am having the same problem and hope that will do the trick.

---

### Post by fragos on 2008-03-20
I don't know off hand if the reader on the front of the 1420 reads xD cards but it works for SDs by just pushing in the plastic plug dummy card so that it pops out to be removed.  Plug in the SD and it will mount automatically.  If you do need a separate xD reader, just plug the reader into a USB and when the xD card is put in the reader it will also auto-mount.

---

