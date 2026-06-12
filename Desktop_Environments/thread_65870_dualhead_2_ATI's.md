---
title: "dualhead 2 ATI's"
date: 2005-09-15
forum: Desktop Environments
---

### Post by trash on 2005-09-15
I am following the howto's found here, all seems pretty straight forward and my end results are promissing as far as config's.. I do get a X starting on term8 when doing the xinit -- :2(though i have read this may not be useful for trouble shooting dualhead setup), but as yet my second ATI 3d rage pro and screen are not doing much.
I'm trying this on my mac and I am starting to wonder if the card is X86 only???? Is this possible?(I do know the card works on x86 machine. So far I've tried the ATI, vesa, vga drivers and xorg log just tells me no driver could be found for the card... here are some details...

xorg log, both cards are seen
(!!) More than one primary device found
(--) PCI: (0:16:0) ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS rev 0, Mem @ 0x94000000/26, 0x90000000/14, I/O @ 0x0400/8, BIOS @ 0xf1000000/17
(--) PCI: (16:20:0) ATI Technologies Inc 3D Rage Pro 215GP rev 92, Mem @ 0x81000000/24, 0x80083000/12, I/O @ 0x0400/8, BIOS @ 0x800a0000/17

xorg.conf
Section "Device"
        Identifier      "Primary"
        Driver          "r128" #"ati"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Device"
        Identifier      "Secondary"
        Driver          "ati"
        BusID           "PCI:10:16:0"
        Option          "UseFBDev"              "true"
EndSection


Section "Monitor"
        Identifier      "Mitsubishi"
        Option          "DPMS"
        HorizSync       56.5
        VertRefresh     70
EndSection

Section "Monitor"
        Identifier      "Idekliyama"
        Option          "DPMS"
        HorizSync       21.9-50
        VertRefresh     50-90
EndSection

Section "ServerLayout"
Identifier "Multihead Layout"
Screen "first" 0 0
Screen "second" RightOf "first"
Option "Xinerama" "On"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

I've heard other mac users using this card so I just assumed it would be compatible. am I wrong on this?
Thanks.

---

### Post by mlomker on 2005-09-15
This:
> 
(--) PCI: (16:20:0) ATI Technologies Inc 3D Rage Pro 215GP rev 92, Mem @ 0x81000000/24, 0x80083000/12, I/O @ 0x0400/8, BIOS @ 0x800a0000/17

Doesn't seem to match this:
```

 BusID "PCI:10:16:0"

```

Try changing it to 16:20:0 ?

---

### Post by trash on 2005-09-15
Trying another Ati card now, but yes I have tried both of those busid's with similar results with both cards... going to try the same setup on my x86 later tonight.
Here are my busid's if this might help. 

kenji@g4:~$ sudo mv /tmp/.X0-lock ~/.X0-lock
kenji@g4:~$ sudo X -scanpci
Probing for PCI devices (Bus:Device:Function)
(0:11:0) Apple Computer Inc. UniNorth 1.5 AGP
(0:16:0) ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
(16:11:0) Apple Computer Inc. UniNorth 1.5 PCI
(16:18:0) unknown card (0x3083/0x0035) using a NEC Corporation USB
(16:18:1) unknown card (0x3083/0x0035) using a NEC Corporation USB
(16:18:2) unknown card (0x3083/0x00e0) using a NEC Corporation USB 2.0
(16:20:0) ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB]
(16:23:0) Apple Computer Inc. KeyLargo Mac I/O
(16:24:0) Apple Computer Inc. KeyLargo USB
(16:25:0) Apple Computer Inc. KeyLargo USB
(32:11:0) Apple Computer Inc. UniNorth 1.5 Internal PCI
(32:14:0) unknown card (0x11c1/0x5811) using a Lucent Microelectronics FW323
(32:15:0) Apple Computer Inc. UniNorth GMAC (Sun GEM)
kenji@g4:~$ sudo mv ~/.X0-lock /tmp/.X0-lock

lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 PCI
0001:10:12.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:12.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:12.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0001:10:14.0 VGA compatible controller: ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB] (rev 9a)
0001:10:17.0 ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Lucent Microelectronics FW323
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)

---

### Post by mlomker on 2005-09-16
[QUOTE=trash]Trying another Ati card now, but yes I have tried both of those busid's with similar results with both cards... going to try the same setup on my x86 later tonight.
[/quote]

I think you're moving into mostly uncharted waters, a power-pc with 2 monitors.  I run amd64 and have similar experiences...things that the 32-bit guys don't have to deal with.

I just thought I'd point out what seemed to be a typo.

---

### Post by trash on 2005-09-16
AH! never even crossed my mind that it might not work the same on a mac or amd64, tho two good things came of trying yet another card(card #3), my xorg log in the mac used the word shared in a line refering to the second card... will post xorg log later.
Second card that is now in the x86 is a better card than i thought! I now get 1280x1024!! yay!
Still haven't tried dual head on the x86 yet but will get to it soon.

Thanks, lemme know if ya make any progress!

---

### Post by trash on 2005-09-16
This is the closest I get, before i was using driver r128 on first card and ati on second card, this output is ati on both cards where as r128 on both cards fails to 'share'.
noted the invalid io allocation but don't have a clue...

(II) Primary Device is:
(II) ATI:  Candidate "Device" section "Primary".
(II) ATI:  Candidate "Device" section "Secondary".
(II) ATI:  Shared PCI/AGP Mach64 in slot 16:20:0 detected.
(II) ATI:  Shared PCI/AGP Mach64 in slot 16:20:0 assigned to active "Device" section "Secondary".
(II) Loading sub module "atimisc"
(II) LoadModule: "atimisc"
(II) Loading /usr/X11R6/lib/modules/drivers/atimisc_drv.o
(II) Module atimisc: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 6.5.6
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.7
(--) Chipset ATI Rage 128 Pro GL PF (AGP) found
(II) Loading sub module "r128"
(II) LoadModule: "r128"
(II) Loading /usr/X11R6/lib/modules/drivers/r128_drv.o
(II) Module r128: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 4.0.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.7
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x00000000 - 0x00000000 (0x1) MX[B]
        [2] -1  0       0xf5200000 - 0xf53fffff (0x200000) MX[B]
        [3] -1  0       0xf5000000 - 0xf5000fff (0x1000) MX[B]
        [4] -1  0       0x80081000 - 0x80081fff (0x1000) MX[B]
        [5] -1  0       0x80082000 - 0x80082fff (0x1000) MX[B]
        [6] -1  0       0x80000000 - 0x8007ffff (0x80000) MX[B]
        [7] -1  0       0x80080000 - 0x800800ff (0x100) MX[B]
        [8] -1  0       0x80084000 - 0x80084fff (0x1000) MX[B]
        [9] -1  0       0x80085000 - 0x80085fff (0x1000) MX[B]
        [10] -1 0       0x800a0000 - 0x800bffff (0x20000) MX[B](B)
        [11] -1 0       0x80083000 - 0x80083fff (0x1000) MX[B](B)
        [12] -1 0       0x81000000 - 0x81ffffff (0x1000000) MX[B](B)
        [13] -1 0       0xf1000000 - 0xf101ffff (0x20000) MX[B](B)
        [14] -1 0       0x90000000 - 0x90003fff (0x4000) MX[B](B)
        [15] -1 0       0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
        [16] -1 0       0x00ffffff - 0x00ffffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [18] -1 0       0x00000400 - 0x000004ff (0x100) IX[B](B)
        [19] -1 0       0x00000400 - 0x000004ff (0x100) IX[B](B)
(WW) ****INVALID IO ALLOCATION**** b: 0x400 e: 0x4ff correcting^G
(II) window:
        [0] -1  0       0x00000000 - 0x00ffffff (0x1000000) IX[B]
(II) resSize:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) IX[B]
(II) window fixed:

---

