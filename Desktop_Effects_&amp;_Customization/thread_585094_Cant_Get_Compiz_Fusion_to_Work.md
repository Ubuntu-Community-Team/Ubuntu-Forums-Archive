---
title: "Cant Get Compiz Fusion to Work"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by R-Dot-Yung on 2007-10-21
So i re-installed 7.04 after a 7.10 disaster...

and now no matter what i do, Compiz Fusions effects just do nothing, compiz gets enabled, i go into the CCSM and turn effects on and nothing is working...

Ive wiped any trace of desktop effects and re-installed all the stuff over twice and nothing is working...

any ideas?

---

### Post by DutyDuty on 2007-10-21
Can you tell us about your graphics card? Are your drivers up-to-date? 

"Nothing is working" isn't very helpful...

---

### Post by R-Dot-Yung on 2007-10-21
Im on a Dell D600...

why wouldnt it work if it was working before...the only thing i had to change before to make it run on this crappy POS was the bit depth from 24 to 16 and i have already done that

---

### Post by DutyDuty on 2007-10-21
Run
```
lspci
```

Post the results.

---

### Post by R-Dot-Yung on 2007-10-22
```
 harrison@harrison-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
harrison@harrison-laptop:~$ 

```

---

### Post by DutyDuty on 2007-10-22
Hmmm...try these, in that order.

```
compiz --replace
```
```
emerald --replace
```

Also, ```
Metacity
``` if you just want your computer to be tolerable.

---

### Post by michael37 on 2007-10-22
> **DutyDuty said:**
> Hmmm...try these, in that order.

```
compiz --replace
```
```
emerald --replace
```

Also, ```
Metacity
``` if you just want your computer to be tolerable.

You have an ATI card.  Try my how-tos in [thread=569654]this thread[/thread].

---

