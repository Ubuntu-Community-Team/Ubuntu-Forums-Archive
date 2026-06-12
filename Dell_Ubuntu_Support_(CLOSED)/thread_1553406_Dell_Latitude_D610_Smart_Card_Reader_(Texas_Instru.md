---
title: "Dell Latitude D610 Smart Card Reader (Texas Instruments PCI6515)"
date: 2010-08-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by k3vmcd on 2010-08-15
I have tried all of the different threads and walkthroughs to try to get my Smart Card reader to work on my Dell Latitude D610 without success.  Please let me know if getting this device to work on Linux/Ubuntu is even possible.  I've put a couple relevant outputs below.  It looks to me like I have a Texas Instruments PCI6515 SmartCard Controller which is not supported by the libraries that I installed while following the threads, which begs the question as to what library does support this reader?  In case it's of any use the Windows driver that I found while trying to get this to work can be found [here]("http://drivers.softpedia.com/get/Other-DRIVERS-TOOLS/Others/Dell-Precision-M20-Texas-Instruments-PCI-6515-Cardbus-Driver.shtml").  This is the last thing that is tying me to Windows as I occasionally need to use my laptop to access DoD websites that require CAC logins.

I am running a fresh install of Ubuntu 10.04 "Lucid Lynx" with all current updates applied.


**lspci:**
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)


**pcsc_scan:**
PC/SC device scanner
V 1.4.16 (c) 2001-2009, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.5.3
Scanning present readers...
Waiting for the first reader...


**Software/Libraries Installed:**
-gscriptor
-libccid
-coolkey
-pcsc-tools
-pcsd
-libpcsclite-dev
-libmusclecard1
-libpcsc-perl
-libckyapplet1
-libpcsclite1

---

### Post by k3vmcd on 2010-08-29
Anyone?

---

