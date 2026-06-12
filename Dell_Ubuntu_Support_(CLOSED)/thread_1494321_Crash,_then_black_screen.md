---
title: "Crash, then black screen"
date: 2010-05-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Xezus on 2010-05-26
hi. i'm having problems with ubuntu on my computer. it seems to run fine, but it randomly becomes unresponsive and brings me to a black screen that says: checking battery state [ok]. Then it goes to a black screen with flashing white vertical lines on the top half of the screen. anyone know how to fix this? i am running ubuntu 10.04 lts 32 bit on a Dell Dimension 2400. 512mb ram. Pentium 4 2.53ghz. and factory integrated intel graphics card. this is very annoying. somebody please help!!!

---

### Post by mikewhatever on 2010-05-27
Can you post the output of lspci from Applications->Accessories->Terminal.

---

### Post by Xezus on 2010-05-27
> **mikewhatever said:**
> Can you post the output of lspci from Applications->Accessories->Terminal.

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

---

### Post by mikewhatever on 2010-05-27
Intel 800 graphics is a known problem. See Lucid release notes.
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Intel%208xx%20X%20freezes/crashes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Intel%208xx%20X%20freezes/crashes)

---

### Post by Xezus on 2010-05-27
> **mikewhatever said:**
> Intel 800 graphics is a known problem. See Lucid release notes.
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Intel%208xx%20X%20freezes/crashes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Intel%208xx%20X%20freezes/crashes)

thank you. you fixed it. for now anyway. hopefully it's permanent.

---

### Post by Richard85 on 2010-05-27
I tried workaround A in the release notes but it only replaced my flashing black and white crash screen with a black crash screen.


00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:0c.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 10)


math315@math315-desktop:~$ dmesg | tail
[ 12.648159] type=1505 audit(1275001798.590:11): operation="profile_load" pid=569 name="/usr/bin/evince-thumbnailer"
[ 12.748081] e100 0000:01:0c.0: firmware: requesting e100/d102e_ucode.bin
[ 12.776363] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 12.780306] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 12.780846] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 12.796101] intel8x0_measure_ac97_clock: measured 52394 usecs (2525 samples)
[ 12.796108] intel8x0: clocking to 48000
[ 22.864021] eth0: no IPv6 routers present
[ 32.532074] end_request: I/O error, dev fd0, sector 0
[ 32.580045] end_request: I/O error, dev fd0, sector 0

math315@math315-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

---

### Post by Dan_Solo on 2010-05-27
I have the same problem on my desktop. 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

---

### Post by Richard85 on 2010-05-28
Xezus, do you mind sharing with me what workaround you used in the release notes?

Thanks!

---

### Post by Rasa1111 on 2010-06-05
Hey peoples,...

 Can any of you having this problem..

please type ```
sudo apt-get update
``` into terminal?
and see if that doesn't fix it?

 I think it might..
[http://ubuntuforums.org/showthread.php?t=1502544](http://ubuntuforums.org/showthread.php?t=1502544)

[http://ubuntuforums.org/showthread.php?t=1494141](http://ubuntuforums.org/showthread.php?t=1494141)

Im hoping...

---

### Post by Richard85 on 2010-06-09
I've done every update for 10.04 since I've upgraded. Computer still crashing.

---

### Post by Xezus on 2010-06-22
> **Richard85 said:**
> Xezus, do you mind sharing with me what workaround you used in the release notes?

Thanks!

Sorry to reply after all this time. It ended up not being fixed. Instead i decided to try opensuse 10.2 with kde as my desktop. It never crashes on my system. I use opensuse on master, and i use ubuntu on my slave drive. ubuntu still crashes though. i could work around it by getting a good graphics card, but i am getting a sony vaio instead. i will use opensuse, ubuntu, and kubuntu on it. you may think that all these os's are unnecessary to have on one laptop, and you are right. i am doing it because i can and i'm bored.

---

### Post by Rasa1111 on 2010-06-22
well mine was doing this numerous times a day, for a couple months,
But it hasnt done it in the past month at least.
all seems fixed on this end.
dunno how though.

---

### Post by ubkid on 2010-12-25
> **Richard85 said:**
> I've done every update for 10.04 since I've upgraded. Computer still crashing.

Two quick questions:

Would buying and installing a new video card solve the problem?  Some are pretty cheap. Recommendations?
I have this problem on both 9.10 and 10.04, and therefore am not sanguine about 10.10 solving it, but does anyone know if it does?

Thanks to all.

---

