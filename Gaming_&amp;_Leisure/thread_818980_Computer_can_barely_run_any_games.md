---
title: "Computer can barely run any games"
date: 2008-06-04
forum: Gaming &amp; Leisure
---

### Post by ImThatNerd on 2008-06-04
I just installed and tried running EnemyTerritory and Army Ops(Americas Army). These games would lag and skip so bad for me that it wasn't even playable. I even thought going to Ubuntu instead of Windows would have freed up some resources. 

But then I installed a game called Urban Terror, and it ran perfect and no skipping at all.

My computer has 768MB of RAM and a 1.8GHz Pentium 4 processor. I have an 8year or so Dell desktop so obviously the video card is not that great. Which might be the main problem. 

So I was just wondering is there a way to tone down the graphics so it can run better or anything else? Also I had no programs or anything going on in the background.

---

### Post by Perfect Storm on 2008-06-05
Which video card do you have?

you could try Nexiuz (fps game) - it's great to scale after computer specs.

---

### Post by ImThatNerd on 2008-06-05
> **Artificial Intelligence said:**
> Which video card do you have?

you could try Nexiuz (fps game) - it's great to scale after computer specs.

Hmm, I will try that game out. Reminds me of Quake. Here are my specs when I ran lspci. I am not sure if this helps. If not let me know.

```
ryan@ryan-desktop:~$ lspci
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
01:08.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
ryan@ryan-desktop:~$ 

```

---

### Post by Perfect Storm on 2008-06-05
Ah, Intel card. Not good for gaming (especially not on linux, and general on any OS).

---

### Post by ardvark71 on 2008-06-05
> **Artificial Intelligence said:**
> Ah, Intel card. Not good for gaming (especially not on linux, and general on any OS).

Hi...

Most likely onboard. :(

@ ImThatNerd...

Do you know if you have an AGP expansion port on your motherboard?

Best Regards...

---

### Post by ImThatNerd on 2008-06-05
I doubt I do ardvark71. I know my Intel card sucks but some games run smooth, but all others run horrible. But I know that varies from game to game. Thanks anyways.

---

