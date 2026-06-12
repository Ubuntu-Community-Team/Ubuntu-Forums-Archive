---
title: "[SOLVED] Bluetooth on Inspiron Mini 9"
date: 2008-10-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wookie81179 on 2008-10-07
Hello,

I've got my "Mini" a couple weeks ago. Installed Ubuntu 8.04 from a USB-Stick, got sound and wireless (with WPA2 via NDISWRAPER) running and working thanks to this forum.

What's not working is the built-in BLUETOOTH and I couldn't find any post regarding that matter here as well.

Sysinfo can't even identify any BLUETOOTH-Devices, only some unknown devices as per attached screenshot.

My lspci-output:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
02:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
02:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
```

My lsusb-ouput:
```
Bus 005 Device 002: ID 0c45:63e5 Microdia
Bus 005 Device 001: ID 0000:0000 
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000  
```

Can anybody help me? Did anyone even encounter a similar problem yet?

Thanks in advance for your help.

---

### Post by deldotb on 2008-10-14
Try this.  
[http://mydellmini.com/forum/hacked-bluetooth-driver-appears-for-dell-mini-9-t155.html](http://mydellmini.com/forum/hacked-bluetooth-driver-appears-for-dell-mini-9-t155.html)

Just got my mini in yesterday.  Have you had any lockup issues with Bluetooth and/or Suspend?

---

### Post by deldotb on 2008-10-14
Sorry dude!  I didn't read... it's for Winders.
I'll look around for something.

---

### Post by wookie81179 on 2008-11-26
**SOLUTION**

Thanks everyone, but I found the solution in this simple post.

[http://ubuntuforums.org/showpost.php?p=6249937&postcount=20](http://ubuntuforums.org/showpost.php?p=6249937&postcount=20)

All I had to do was install the "Aircraft Manager" and put an "X" in the "Enable Bluetooth"-Field.

Bye

---

