---
title: "UT2004 won't start"
date: 2007-06-14
forum: Gaming &amp; Leisure
---

### Post by TaylorHelferty on 2007-06-14
I just installed UT2004 on my Ubuntu laptop, then updated it to version 3369. I never did try it out before updating so I don't know if it would've given me the same error. It gives me this error and then won't start: "Couldn't set video mode: Couldn't find matching GLX visual."

Anyone know what that means or how to make it work?

Thanks in advance.

---

### Post by TaylorHelferty on 2007-06-14
Excuse the double post, but I couldn't find the edit button, if there even is one.

I thought I'd also add to this thread another game-related question, instead of making two threads. The other question is, I just downloaded and installed Tremulous, but it won't start either. The screen goes black for almost a second and then goes back to the desktop and nothing else happens. Any ideas?

Edit: found the edit button, just didn't see it because I forgot I wasn't logged in at the time. Been a long day . . .

---

### Post by tgm4883 on 2007-06-14
do "glxinfo | grep direct" in the terminal and post the output

---

### Post by TaylorHelferty on 2007-06-14
direct rendering: no
OpenGL renderer string: Mesa GLX Indirect

---

### Post by tgm4883 on 2007-06-14
what kind of video card?

---

### Post by TaylorHelferty on 2007-06-14
I honestly don't know. Got this laptop second hand. I fixed Tremulous though by typing at the end of the launch command "+set r_allowSoftwareGL 1" and it came on. Didn't work for UT2004 though, just said "+set could not be found" or something. Maybe something similar to type in the command?

---

### Post by tgm4883 on 2007-06-14
post the output of "lspci"

---

### Post by TaylorHelferty on 2007-06-14
00:00.0 Host bridge: ALi Corporation M1672 Northbridge [CyberALADDiN-P4]
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:09.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 USB Controller: NEC Corporation USB (rev 43)
00:0c.1 USB Controller: NEC Corporation USB (rev 43)
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:10.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

---

### Post by tgm4883 on 2007-06-14
Well here is what I found on your card, it doesn't look good.

[http://ubuntuforums.org/showthread.php?p=1890499](http://ubuntuforums.org/showthread.php?p=1890499)

You need to install the 3d drivers for your card.  Where you can get those, I don't know

---

