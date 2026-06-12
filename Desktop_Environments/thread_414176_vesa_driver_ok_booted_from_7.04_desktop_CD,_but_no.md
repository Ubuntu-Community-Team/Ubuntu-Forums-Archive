---
title: "vesa driver ok booted from 7.04 desktop CD, but not when installed"
date: 2007-04-19
forum: Desktop Environments
---

### Post by pgdh on 2007-04-19
I have an ASUS M2V-MX mobo which uses the via K8M890 chip for to provide onboard graphics. I have installed an Athlon 64 X2 3600+ and 2GB of RAM.

When I boot from the ubuntu-7.04-desktop-i386.iso, the VESA driver works a treat (much faster than under 6.10).

But when I install from the same CD, and use the very same xorg.conf, the VESA driver bombs out ...

basket# diff boot*/Xorg.0.log
6c6
< Current Operating System: Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
---
> Current Operating System: Linux pgdh-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
14c14
< (==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr 19 21:34:17 2007
---
> (==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr 19 23:07:23 2007
407,411c407,413
< (II) VESA(0): Primary V_BIOS segment is: 0xc000
< (II) VESA(0): VESA BIOS detected
< (II) VESA(0): VESA VBE Version 3.0
< (II) VESA(0): VESA VBE Total Mem: 65536 kB
< (II) VESA(0): VESA VBE OEM: VIA K8M890CE
---
> (EE) VESA(0): V_BIOS address 0x1010 out of range
> (II) UnloadModule: "vesa"
> (II) UnloadModule: "vm86"
> (II) Unloading /usr/lib/xorg/modules//libvm86.so
> (II) UnloadModule: "int10"
> (II) UnloadModule: "vbe"
> (EE) Screen(s) found, but none have a usable configuration.
413,3322c415,416
< (II) VESA(0): VESA VBE OEM Software Rev: 1.0
< (II) VESA(0): VESA VBE OEM Vendor: 
< (II) VESA(0): VESA VBE OEM Product: 
< (II) VESA(0): VESA VBE OEM Product Rev: 
< (**) VESA(0): Depth 24, (--) framebuffer bpp 32
< (==) VESA(0): RGB weight 888
< (==) VESA(0): Default visual is TrueColor
.
.
.
< Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
< Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
---
> Fatal server error:
> no screens found

The root of the problem seems to be related to that "(EE) VESA(0): V_BIOS address 0x1010 out of range".

Trouble is, I have no idea where to go from here. Any ideas?

And why does it work when booted form the CD, but not when booted from the disk installed from the same CD?

Yes, I know there's a VIA driver available, but at the moment it is only available in source form for the K8M890, and I'd be perfectly happy if I could get the VESA driver working of the installed image as well as it does off the CD.

Failing, this I'll be looking for a PCI/PCIEX16 graphics card, or another mobo :(

Phil

---

### Post by dorath on 2007-04-19
Something similar happens to me, though with an nVidia card.  However, I believe it's actually due to the native resolution of my LCD monitor, 1280x1024.  If you have an LCD monitor with the same native resolution, then perhaps what works for me will also work for you.  If you do not, then please disregard my reply.

Try this:
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-org
```You'll be asked to select a resolution and a video driver.  Here is where I must select 1280x1024, and where you should select the native resolution for your monitor.  Next select VESA.  After you have reconfigured:```
 sudo /etc/init.d/gdm start
```If all goes well, you'll get your desktop.  Again, I don't have a VIA, but your symptoms sound very similar to mine.

Best of luck!

---

### Post by bluewagon on 2007-04-19
will this work with X server failing as well? i saw some posts about people asking users with the problem to do something similar to that

---

### Post by pgdh on 2007-04-20
Thanks for the suggestion, but that didn't fix it (even with s/xserver-org/xserver-xorg/)

I guess there is something broken in the way the FB is being mapped. I'm still intrigued by the fact that it works when I boot directly off the 7.04 Desktop CD, so I'm just off to reinstall from the alternate install CD.

Please keep the suggestions coming. I will also post updates as I home in on the problem.

Phil

---

### Post by pgdh on 2007-04-20
SORTED!

I just installed from the Ubunto 7.04 Alternate i386 CD, and now I can boot into a working X server.

I guess installing of the Desktop CD is broken in some subtle way.

Phil

---

