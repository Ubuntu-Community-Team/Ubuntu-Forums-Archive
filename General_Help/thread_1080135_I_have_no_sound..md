---
title: "I have no sound."
date: 2009-02-25
forum: General Help
---

### Post by planet-reptile on 2009-02-25
This is what get in the terminal

kim@kim-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 064a (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
05:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
kim@kim-laptop:~$

The sound has worked in Vista, so i know it works, but not at the moment.

Hope someone can help.

---

### Post by linux_tech on 2009-02-25
In terminal type:
```

cat /proc/asound/card0/codec#* | grep Codec
aplay -l

```
post output

---

### Post by planet-reptile on 2009-02-25
Hi.

This is the output from the terminal

kim@kim-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC889
Codec: LSI ID 1040
Codec: Generic 10de ID 6
kim@kim-laptop:~$ aplay -l


Edit:
BTW my laptop is an
Acer Aspire 8930G
Intel Core 2 Duo processor P8600
2.4GHz, 1066MHz FSB
4gb DDR3
Nvidia 9700M GT

---

### Post by zeroemissions on 2009-02-25
I had the exact same problem

type 

alsamixer

into terminal and then adjust the volumes to max and unmute the master.

Edit, this opens a GUI but I had to use the arrow keys to select different chanels. Hit 'M' to toggle mute and 'H' for help.

---

