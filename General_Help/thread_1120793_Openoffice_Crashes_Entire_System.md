---
title: "Openoffice Crashes Entire System"
date: 2009-04-09
forum: General Help
---

### Post by Irony on 2009-04-09
Okay people, solve this one;

Processor		AMD Athlon(tm) 64 Processor 3500+
Memory			2076MB (299MB used)
Operating System	Debian GNU/Linux 5.0 (LXF118)
radeon			ATI Radeon
card			Radeon X800PRO

also

Operating System	Linux Mint 6/Elyssa (LXF116)

With Debian 5 running repository versions of OOo 2.4 and OOo 3.0 causes a total screen freeze after a few minutes - keys are unresponsive (Ctrl+Alt+Backspace, etc), mouse cursor moves slowly.

A hard reboot (pressing reset button on the tower) is required.

Exactly the same happens on Linux Mint 6 OOo 2.4 (another partition).

Running OOo 3 from the debs in a linux format disc (LXF113) does not cause a crash on Debian 5, however this has no spell checking function - adding a dictionary extension to theses debs (Tool > Extension Manager) causes an immediate total screen freeze to the ... keys are unresponsive (Ctrl+Alt+Backspace, etc), mouse cursor moves slowly. A hard reboot (pressing reset button on the tower) is required. I don't know if this a separate type of crash to that shown with the repository OOos.

I've used OOo successfully on this machine with previous installs of Ubuntu and other Linux distros, the key difference being that with them I use the restricted driver because Blender and Googleearth would not run without the restricted driver (indeed in some cames the distros would be too unstable to run without the restricted driver).

With Linux Mint 6 the restricted driver doesn't work (I haven't tried it on Debian 5 yet) but in both distros Blender and Googleearth work with the opensource radeon drivers... but the repository OOos don't (only OOo 3 from LXF113, which also causes a system seize up if I add a dictionary extension).

My assumption is that OOo is interacting badly with the open source radeon drivers on my system. I want to get the repository versions of OOo working on my system.

Note, ticking OpenGL in OOo makes no difference.

The crashes have happened when I have had writer open, though sometimes calc is also open.

Any thoughts? Is it radeon is it Openoffice?

Here is the last section of the latest crash log from Linux Mint 6 /var/log/Xorg.0.log;

```
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: T611759RBBZR
(II) RADEON(0): Monitor name: DELL 1905FP
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac0d40525a4242
(II) RADEON(0): 	280f010380261f78ee1145a45a4aa024
(II) RADEON(0): 	145054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00543631
(II) RADEON(0): 	313735395242425a520a000000fc0044
(II) RADEON(0): 	454c4c203139303546500a20000000fd
(II) RADEON(0): 	00384c1e510e000a20202020202000ac
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16397
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
```

---

### Post by cmnorton on 2009-04-09
What about CTRL+ALT+F1 and logging in as an X-term? Does that work?

---

### Post by Irony on 2009-04-09
The keys are totally unresponsive - only a hard reboot works, i.e. pushing the reset button on my tower.

---

### Post by cmnorton on 2009-04-09
The only things that come to mind are to look in your logs (/var/log) after rebooting, and outputting dmesg. It sounds like graphics, and reconfiguring X would depend on how your configured now and the kind of graphics chip you have installed.

---

### Post by Irony on 2009-04-09
Yes the last section of my Xorg is listed in my very first post.

---

### Post by Irony on 2009-04-09
And here is the last bit of my /var/log/gdm/0.log;

```
AUDIT: Thu Apr  9 11:02:43 2009: 5098 X: client 4 rejected from local host ( uid=0 gid=0 pid=5276 )
AUDIT: Thu Apr  9 11:02:51 2009: 5098 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5280 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Thu Apr  9 11:02:51 2009: 5098 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5281 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Thu Apr  9 11:02:51 2009: 5098 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5282 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
Dac detection success
in RADEONProbeOutputModes
Dac detection success
in RADEONProbeOutputModes
Dac detection success
in RADEONProbeOutputModes
Dac detection success
in RADEONProbeOutputModes
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Duplicate shape name ""
>                   Using last definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
> Warning:          Multiple doodads named ""
>                   Using first definition
Errors from xkbcomp are not fatal to the X server
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
```

---

### Post by Irony on 2009-04-17
It turns out that in Debian 5 I had to install the restricted drivers for my X800 card following the intructions here;

[http://wiki.cchtml.com/index.php/Debian_Installation_Guide](http://wiki.cchtml.com/index.php/Debian_Installation_Guide)

Pressing the restricted drivers icon in Linux Mint 6 (and Ubuntu 8.10) installs the drivers but on rebooting I get the error;

```
(EE) fglrx(0): DRIScreenInit failed!
(EE) fglrx(0): FB pci_device_map_range error!
(EE) fglrx(0): Failed to map FB memory
(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
```

Perhaps I need to follow the Debian instructions to install successfully in Ubuntu?

---

