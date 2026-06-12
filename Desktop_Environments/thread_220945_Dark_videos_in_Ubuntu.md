---
title: "Dark videos in Ubuntu"
date: 2006-07-22
forum: Desktop Environments
---

### Post by seshomaru samma on 2006-07-22
Wenever I play video (wmv/avi) files they becoming darker and darker no matter what video player I use to view them. When I reboot the problem is solved , but after a while it comes back.
I checked the same videos on Fedora and had no problems.
What can I do ?

---

### Post by syxbit on 2006-07-22
> **seshomaru samma said:**
> Wenever I play video (wmv/avi) files they becoming darker and darker no matter what video player I use to view them. When I reboot the problem is solved , but after a while it comes back.
I checked the same videos on Fedora and had no problems.
What can I do ?

do you have an ati video card ?

---

### Post by seshomaru samma on 2006-07-22
no
```
sesho@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Co ntroller/Host-Hub Interface (rev 01)
0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G] /GE Chipset Integrated Graphics Device (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EH CI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interfa ce Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev  01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus  Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH 4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:01:05.0 Communication controller: Conexant: Unknown device 2702 (rev 01)
0000:01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01 )

```

---

### Post by syxbit on 2006-07-22
you could try reinstaling your codecs, but it sounds like it's your video card
if i were you i'd buy a cheap nvidia gfx card (assuming it's a desktop)
i had an ati and had major troubles with dvd playback.
you should also try VLC.
i've had more luck with that

---

