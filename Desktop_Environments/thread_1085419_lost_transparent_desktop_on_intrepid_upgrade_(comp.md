---
title: "lost transparent desktop on intrepid upgrade (compiz)"
date: 2009-03-03
forum: Desktop Environments
---

### Post by mageus on 2009-03-03
In Hardy, I had transparency set to 50% in the CCSM Desktop Cube->Transparent Cube section.  When I upgraded to Intrepid, the desktop is opaque (can't get compiz cube transparency to work).

- Yes, gconf-editor still shows apps->nautilus->preferences->show_desktop = false
- No, CCSM->Desktop Cube->Transparent Cube->'Transparency Only on Mouse Rotate' is not enabled

This happens in 32 & 64 bit.  Can't seem to get this to work.

Any ideas?

---

### Post by joten on 2009-03-04
Same effect after update of xorg videodrivers today, yesterday still had transparency. Also lost cube deformations cylinder or sphere not working anymore. i'm using ATI drivers (proprietary) with Radeon HD 3850. Seems to be driver related.

---

### Post by mageus on 2009-03-05
So, you're suggesting this is an xorg issue?

I've got an nvidia 9800GT running the proprietary 180.11 drivers.

---

### Post by joten on 2009-03-09
Hm, don't know, found that after restart it worked until i got a
" compiz.real[8367]: segfault at 8 ip b7aeab7e sp bfc90344 error 6 in libc-2.8.90.so[b7a79000+158000]"
in dmesg then trasparency was gone

---

### Post by mageus on 2009-03-10
These were my setups:

- Hardy 32-bit & 64-bit - transparency worked
- Intrepid 64-bit NV 7600GT 177.82 - no transparency
- Intrepid 64-bit NV 9800GT 180.11 - no transparency
- Intrepid 64-bit NV 9800GT 180.35 - no transparency
- Intrepid 32-bit NV 9800GT 180.11 - no transparency

Considering the problems with Compiz & KDE 4.2 apps, the new xorg, it's anyone's guess where the problem lies.

I've just switched back to Metacity until all this gets figured out.

---

### Post by WooSkadoo on 2009-08-11
Heyyyyy, sorry to bump such an old thread, but this has been driving me crazy for a while. I finally realized it was losing transparency because my desktop icons weren't there... type

```
nautilus show_desktop
```

in Terminal and BAM! See-thru desktop!

---

