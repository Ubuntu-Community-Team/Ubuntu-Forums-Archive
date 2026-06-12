---
title: "KDE hangs - nepomukservicesstub - 'Failed to idle channel 1'"
date: 2013-03-17
forum: Desktop Environments
---

### Post by getnitin15 on 2013-03-17
Hello everyone!

I just installed ubuntu 12.10 and KDE over it. For the first week my system works as butter.

But suddenly I have started experience hangs/crashes. After approsimately 15-20 minutes of usage my system hangs and I get the subjected error message. Only option left after this is hard reset!!! Please help

At system startup i get a warning message that ubunut had an internal error and the error details show:

/usr/bin/nepomukservicestub is the thing that crashed. have already sent a bug report as it asks me.


/var/log/syslog snippet:
502-Mar 17 10:17:37 nitin-desktop-ubuntu anacron[914]: Job `cron.weekly' started
579-Mar 17 10:17:37 nitin-desktop-ubuntu anacron[3689]: Updated timestamp for job `cron.weekly' to 2013-03-17
685-Mar 17 10:17:45 nitin-desktop-ubuntu anacron[914]: Job `cron.weekly' terminated
765-Mar 17 10:17:45 nitin-desktop-ubuntu anacron[914]: Normal exit (2 jobs run)
841-Mar 17 10:18:58 nitin-desktop-ubuntu kernel: [  698.228284] [drm] nouveau 0000:01:00.0: cal_space: -16
944:Mar 17 10:19:08 nitin-desktop-ubuntu kernel: [  708.784008] [drm] nouveau 0000:01:00.0: **Failed to idle channel 1.**
1058-Mar 17 10:19:08 nitin-desktop-ubuntu kernel: [  708.836288] show_signal_msg: 45 callbacks suppressed
1159-Mar 17 10:19:08 nitin-desktop-ubuntu kernel: [  708.836294] QThread[2020]: **segfault at 0 ip**   (null) sp b3328aac error 14 in **nepomukservicestub**[8048000+7000]

Please help if someone knows about this. 

Its frustrating and I don't want to reinstall KDE.

systemstats:

lspci output:
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82G33/G31/P35/P31 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IH (ICH9DH) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation NV44 [GeForce 7100 GS] (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b2)
07:01.0 Serial controller: Device 4348:3253 (rev 10)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]


Thanks


Nitin

---

### Post by hainen on 2013-03-17
Not that I understand the message but my guess is that somthing that involve nouveau probably is problem with the nouveau driver. Have you tried the closed Nvidia driver?

---

### Post by getnitin15 on 2013-03-17
Not yet. Let me try and get back ! Thanks .

---

### Post by getnitin15 on 2013-03-25
Installing NVIDIA closed driver works. Thanks.!

$sudo apt-get --install nvidia-current.

Thread can be closed.

---

