---
title: "[intrepid][upgrade] intel i865 breaks, reverts to vesa on upgrade from 8.04 to 8.10"
date: 2008-12-15
forum: General Help
---

### Post by sloggerkhan on 2008-12-15
I upgraded from 8.04 to 8.10 the other day, though it went fine at first but rebooted and turns out my x is broken. I was using the intel i865 or i810 driver on hardy, but now on gutsy they're part of the intel driver.

If I put intel as the driver in xorg.conf it won't work and has a message about failing to open displays. If I sudo dpkg-reconfigure xserver-xorg, it goes to the vesa driver. If I halt X and to sudo Xorg -configure it dies with some error about Loading /usr/lib/xorg/modules/drivers//vga_drv.so, becuase it passes over the intel driver when trying to load drivers. If I get rid of all xorg.confs, it does try to use the intel driver with a confless configuration, but that also fails.

In short, how do I get hardy to use the intel xorg driver instead of vesa?

(I think this may have occurred because I think i810 and i865 drivers used to be in separate packages from the intel driver.)

Anycase, help is appreciated.

---

### Post by sloggerkhan on 2008-12-17
Help! I'm also having this problem with Arch!
It seems that with the current intel driver using the i865 hardware xorg thinks that the interfaces it has are tmds and vga, when in reality the only display connector is dvi (IE probably not tmds) so things break. I can't seem to force the monitor to use an interface that agrees with the graphics...

---

