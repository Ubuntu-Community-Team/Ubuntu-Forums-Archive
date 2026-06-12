---
title: "ATI 128 Pro 3D support"
date: 2006-03-02
forum: Desktop Environments
---

### Post by stepore on 2006-03-02
Hey folks,

Just wondering if an ATI 128 pro (all in wonder) is newer than a  RADEON
8500 card. From ATI's website it has drivers for linux and says, "for
RADEON 8500 Series cards and higher." So, i wanted to know if the ATI
128 pro is higher and if i'll get 3D support for this card?

I plan to run Ubuntu on this used PC with the ATI
card, will the xorg-driver-fglrx package give this card 3D support? It
also doesn't mention if the ATI 128 pro is supported.

cheers.

---

### Post by RAOF on 2006-03-02
The ATI 128 pro is older than all the radeon cards.

I'm not sure, but it seems that the r128 driver ([man page here]("http://ftp.x.org/pub/X11R6.9.0/doc/html/r128.4.html")) should support your card.

---

### Post by stepore on 2006-03-02
[QUOTE=RAOF]I'm not sure, but it seems that the r128 driver ([man page here]("http://ftp.x.org/pub/X11R6.9.0/doc/html/r128.4.html")) should support your card.[/QUOTE]

By support, do you mean that the card/display will just work, or that it'll have hardware acceleration (3d) support?

cheers.

---

### Post by RAOF on 2006-03-02
I believe, from what I've read in the Dapper forum, that it will also provide 3D support.  In fact, enough 3D support to run Xgl :)

---

### Post by stepore on 2006-03-03
[QUOTE=RAOF]I believe, from what I've read in the Dapper forum, that it will also provide 3D support.  In fact, enough 3D support to run Xgl :)[/QUOTE]

WOW, didn't expect that. All i wanted was to run tuxracer.

thanks for the info.
cheers.

---

### Post by az on 2006-03-03
I have a few of them.  For cards with less than 16 megs of memory, you may have to configure X to use a smaller color depth, or a smaller screen resolution.  Ubuntu configures your card to use the maximum resolution and color depth.  Xorg needs to allocate memory for dri and cannot do that on-the-fly.

You may have to boot into recovery mode and run

dpkg--reconfigure xserver-xorg and pick 1024x768 as the maximum resolution or 16-bit as the maximum color depth for dri to work.

In breezy, there was still a memory leak which resulted in the occasional glitch on screen.

---

### Post by stepore on 2006-03-04
[QUOTE=azz]I have a few of them.  For cards with less than 16 megs of memory, you may have to configure X to use a smaller color depth, or a smaller screen resolution.[/QUOTE]

i think it has 32MB; lspci:
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS (prog-if 00 [VGA]) Subsystem: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS Flags: bus master, stepping, 66MHz, medium devsel, latency 64, IRQ 11
Memory at d8000000 (32-bit, prefetchable) [size=64M]

i'm not sure how to get 3d support though. i have the r128 driver listed in /etc/X11/xorg.conf (instead of the ati driver) but there's probably more to do:

amdshine@amdubuntu:~$ glxinfo |grep rendering
direct rendering: No

what else do i need to add to xorg.conf to make this work. i tried tuxracer and it's pretty slow and no fonts show up, also no music/sound.

---

### Post by az on 2006-03-04
> **stepore]i think it has 32MB said:**
> ) Subsystem: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS Flags: bus master, stepping, 66MHz, medium devsel, latency 64, IRQ 11
Memory at d8000000 (32-bit, prefetchable) [size=64M]

i'm not sure how to get 3d support though. i have the r128 driver listed in /etc/X11/xorg.conf (instead of the ati driver) but there's probably more to do:

amdshine@amdubuntu:~$ glxinfo |grep rendering
direct rendering: No

what else do i need to add to xorg.conf to make this work. i tried tuxracer and it's pretty slow and no fonts show up, also no music/sound.

what does 
cat /var/log/Xorg.0.log|grep EE
show?

---

### Post by stepore on 2006-03-04
[QUOTE=azz]what does 
cat /var/log/Xorg.0.log|grep EE
show?[/QUOTE]

amdshine@amdubuntu:~$ cat /var/log/Xorg.0.log|grep EE
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) R128(0): No DFP detected

i believe i have it working now. i did some googling and added "dri" to the Modules field. Although i still get these errors when i run glxinfo |grep render:

libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
direct rendering: Yes
OpenGL renderer string: Mesa DRI Rage 128 Pro 20041026 AGP 1x

glxgears gives me the same errors:
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30

and it doesn't give me a fps count.

---

