---
title: "no display on reboot and live cd"
date: 2009-06-15
forum: General Help
---

### Post by thesheff17 on 2009-06-15
I have this video card:

EVGA 01G-P3-N959-TR GeForce 9500 GT 1GB 128-bit GDDR2 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card - Retail

I'm installing Ubuntu 9.04 AMD Desktop and with both monitors plugged in I get the splash and bios screen but as soon as it goes to the GDM I don't get a display.  The work around I have right now is that I unplug the Primary display and then everything will show up fine on the secondary monitor.  I don't see any problems in the logs and not sure what else to try.

Maybe GDM is the wrong word but I never get to the Desktop/login screen regardless of booting of the cd or booting off the hard drive.
Here is my lspci


thesheff17@thesheff17-Desktop2:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G35 Express DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82G35 Express PCI Express Root Port (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1)
04:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
05:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

---

### Post by thesheff17 on 2009-11-02
Bump.  This problem still exists with Ubuntu 9.10 AMD 64 bit.  Unplugging a monitor every time I need to boot is a pain.  Anyone have any ideas?  Let me know and I will post any other logs files.

---

### Post by herbertg on 2009-11-08
I'm having all sorts of problems with it also. Not only the problem stated above but screen going black and coming back on every couple of minutes.

---

### Post by thesheff17 on 2009-11-08
herbertg,

I think you are having different issues that I'm not having.  Basically my monitor will only work when I only have the second video adapter plug into the monitor.  You sound more like you are having problems with hardware.  Do you see anything in the logs?  

Let me know and I can help you out.

---

### Post by thesheff17 on 2009-12-10
Well I installed the the most recent nvidia drivers and ran all updates on ubuntu 9.10 and this finally fixed this issue.  I'm not 100% which fixed it but I'm glad I don't have to deal with such a minor inconvenience anymore.

---

