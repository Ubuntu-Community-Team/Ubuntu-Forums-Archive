---
title: "My logs are getting flooded Use 'setkeycodes e055 &lt;keycode&gt;' to make it known."
date: 2008-01-18
forum: Development CD/DVD Image Testing
---

### Post by jaakan on 2008-01-18
jaakan@jms1000:/var/log$ uname -a
Linux jms1000 2.6.24-4-generic #1 SMP Mon Jan 14 18:19:11 UTC 2008 x86_64 GNU/Linux
jaakan@jms1000:/var/log$ 


-rw-r-----  1 101   4  22M 2008-01-18 22:07 messages
-rw-r-----  1 101   4  22M 2008-01-18 22:07 kern.log
-rw-r-----  1 101   4  23M 2008-01-18 22:07 syslog
-rw-r-----  1 101   4  37M 2008-01-18 07:39 messages.0
-rw-r-----  1 101   4  37M 2008-01-18 07:39 kern.log.0
-rw-r-----  1 101   4  37M 2008-01-18 07:39 syslog.0

jaakan@jms1000:/var/log$ tail messages
Jan 18 22:10:35 jms1000 kernel: [22015.348370] atkbd.c: Unknown key released (raw set 2, code 0xd5 on isa0060/serio0).
Jan 18 22:10:35 jms1000 kernel: [22015.348373] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
Jan 18 22:10:36 jms1000 kernel: [22015.844019] atkbd.c: Unknown key pressed (raw set 2, code 0xd5 on isa0060/serio0).
Jan 18 22:10:36 jms1000 kernel: [22015.844026] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
Jan 18 22:10:36 jms1000 kernel: [22015.851348] atkbd.c: Unknown key released (raw set 2, code 0xd5 on isa0060/serio0).
Jan 18 22:10:36 jms1000 kernel: [22015.851354] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
Jan 18 22:10:37 jms1000 kernel: [22016.713411] atkbd.c: Unknown key pressed (raw set 2, code 0xd5 on isa0060/serio0).
Jan 18 22:10:37 jms1000 kernel: [22016.713416] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
Jan 18 22:10:37 jms1000 kernel: [22016.728050] atkbd.c: Unknown key released (raw set 2, code 0xd5 on isa0060/serio0).
Jan 18 22:10:37 jms1000 kernel: [22016.728056] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
jaakan@jms1000:/var/log$ 

I think this might be related to my wireless

/usr/share/hotkey-setup/atkbd.hk
setkeycodes	e055	$KEY_RESERVED

/usr/share/hotkey-setup/dell.hk
#setkeycodes	e008	$KEY_		# Fn+F2		Wireless (e008)


Dell Vostro 1000
AMD64 x2
1Gb ram
wireless is BCM4311

jaakan@jms1000:/var/log$ sudo lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
jaakan@jms1000:/var/log$

any one else getting this?

---

### Post by feminaexlux on 2008-02-02
Exact same problem, I too have a vostro 1000. Not sure what I can do about it.

_[This looks promising?]("http://ubuntuforums.org/showthread.php?t=119499")_

---

### Post by cdtech on 2008-02-02
> **feminaexlux said:**
> Exact same problem, I too have a vostro 1000. Not sure what I can do about it.

_[This looks promising?]("http://ubuntuforums.org/showthread.php?t=119499")_

Did this help you?

---

### Post by Toon Macharis on 2008-09-04
> **feminaexlux said:**
> Exact same problem, I too have a vostro 1000. Not sure what I can do about it.

_[This looks promising?]("http://ubuntuforums.org/showthread.php?t=119499")_

I have a Vostro 1000 also and had exactly the same problem.  The problem is not with Ubuntu, but with the BIOS of Dell that constantly sends a bad battery signal.  The "bad battery" signal is an unknown key and therefore that this is logged.

What I did to solve it:
* start up my Windows (I have a dual boot)
* go to the website of dell
* download the BIOS update for Vostro 1000
* install BIOS version 2.6.3 (before I had 2.4.1)
* shut down my computer
* take out the battery and put it in again
* restart my computer in Ubuntu

and the problem was gone

---

### Post by manicnerd on 2008-09-06
> **Toon Macharis said:**
> I have a Vostro 1000 also and had exactly the same problem.  The problem is not with Ubuntu, but with the BIOS of Dell that constantly sends a bad battery signal.  The "bad battery" signal is an unknown key and therefore that this is logged.

What I did to solve it:
* start up my Windows (I have a dual boot)
* go to the website of dell
* download the BIOS update for Vostro 1000
* install BIOS version 2.6.3 (before I had 2.4.1)
* shut down my computer
* take out the battery and put it in again
* restart my computer in Ubuntu

and the problem was gone

I started getting this message today...I was already at BIOS version 2.6.3 but figured I'd try this anyway.  To my surprise it worked.  Thanks!

**EDIT:** problem/annoyance came back today...

---

### Post by syga on 2009-09-28
I know this is an old thread, but I had the same problem. 

I did some googling, and fixed the problem by going into the bios settings and disabling the hotkey for wireless switch.

---

