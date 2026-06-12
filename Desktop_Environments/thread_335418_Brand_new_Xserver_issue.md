---
title: "Brand new Xserver issue"
date: 2007-01-10
forum: Desktop Environments
---

### Post by glenndavy on 2007-01-10
hi all - Im running a sony vaio (vgn tx-17).  It has an 11.1" screen which is 1366x768, on a i915 chipset.  I have aiglx configured. It has been running fine in gnome and kde for eons with and without beryl.  After dist-upgrade this morning, I get these xorg probs:

- From a reboot gdm (or kdm) start fine.
- If I log in to _any_ window manager as myself (gnome,kde, openbox, wamiea, windowlab, bla) my lcd screen goest to a squarish resolution - presumably 1024x768 instead of taking up whole screen (1366x768). 
- If I log into as root (which I enabled in gdm) everything works fine i.e. I get full 1366x768 resolution 
- If I disable gdm, reboot and login as myself, I can type X and get a full 1366x768 all too familiar X background root window - yay!
- If I try this with xinit or startx X crashes
- regardles of how start x when logged inas myself, the log file contains " DRIScreenInit Failed Disabling DRI". When I login as root DRI and AIGLX all initialise fine according to logs, and eveything works find.
- Often but not always when I try and run X, startx, xinit a second or 3rd time X crashes after first initialising display, and says "VBE Initialisation failed"


There is a back trace provided after the crash:
0: /usr/bin/X11/X(xf86SigHandler+0x81) [some hex address]
1: [some other hex address]
2: /usr/bin/X11/X(InitOutput+0x9c2) [some other hex address]
3: /usr/bin/X11/X(main+0x276) [some other hex address]
4:/lib/tls/i686/cmove/libc.so.6(__libc_start_main+0xdc) [some other hex address]
5: /usr/bin/X11/X(FontFileCompleteXLFD+0xa1) [some other hex address]

seems I need to be root to run X - which suggests the problem is easily fixed - any ideas how?


Thanks

Glenn](*,) 

-

---

### Post by glenndavy on 2007-01-10
bump - anyone else got a similar problem - i.e. only root can run X in all video modes?

---

