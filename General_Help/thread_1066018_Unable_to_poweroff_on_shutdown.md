---
title: "Unable to poweroff on shutdown"
date: 2009-02-10
forum: General Help
---

### Post by ndlarsen on 2009-02-10
Hello all.

Running xubuntu 8.10 intrepid on an Acer Travelmate 4500 series laptop. I'm unable to power it off on shutdown. When changing tty, there's a message saying "acpid: exiting". Here's what I have tried so far.

- booted with both noacpi and acpi=off
- added apm power_off=1 to /etc/modules
- added %powerdev lapslave=/usr/sbin/xfsm-shutdown-helper to /etc/sudoers and the user to the group powerdev
- eventually tried both down- and upgrading the kernel, recenr earlier versions had same issue, the 2.6.28 based didn't but introduced another problem (rendering battery/power monitoring useless)

```
ndlarsen@lapslave:~$ uname -a
Linux lapslave 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

```
```
ndlarsen@lapslave:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
```
Got multiple entries like this in dmesg:
```
[ 4357.340268] ACPI: EC: non-query interrupt received, switching to interrupt mode
```
One of my tty's gives this:
```
halt&#65306;unable to iterate IDE devices: No such files or directory
```

Any ideas will be greatly appreciated. Cheers.

---

### Post by plucky on 2009-02-10
My test system with intrepid would only turn off when I added **acpi=force** to the kernel line in menu.lst.

The system is a lot older than yours as it is a pentium 3 but it now turns off.


Good Luck

---

### Post by ndlarsen on 2009-02-11
I appreciate your reply. Unfortunately this makes no difference.

---

