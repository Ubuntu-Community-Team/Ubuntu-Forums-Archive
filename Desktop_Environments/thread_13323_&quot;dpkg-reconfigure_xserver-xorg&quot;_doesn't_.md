---
title: "&quot;dpkg-reconfigure xserver-xorg&quot; doesn't change my /etc/X11/xorg.conf"
date: 2005-01-30
forum: Desktop Environments
---

### Post by mr_ed on 2005-01-30
I remember hearing that dpkg-reconfigure won't change my conf file, so I followed some other instructions that I saw somewhere...
something like

sudo md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum
dpkg-reconfigure xserver-xorg

but the /etc/X11/xorg.conf remains unchanged.  :(  Any ideas?

---

### Post by az on 2005-01-30
Did you enter different values?

---

### Post by mr_ed on 2005-01-31
I had changed values, yes.

My Radeon 7500 went south :( so I replaced it with my old 3dfx Voodoo3 2000, and I'm trying to get DRI working.
So I ran xorgconfig, and that didn't help, so I figured I'd just try running the Debian tool for it.

Anyway, when I run dpkg-reconfigure xserver-xorg, I can see all the things I've changed (for example, the Video card string is "3dfx Voodoo3 2000"), but in the xorg.conf file has "3dfx***** (generic)"

I'm running Hoary and I changed the XF86Config-4 file to xorg.conf. 

There was actually no xorg.conf.md5sum in the /var/lib/xfree86/ folder in the first place.  Maybe I should rename it back to XF86Config-4, reset the md5sum, and then run dpkg-reconfigure again?

---

