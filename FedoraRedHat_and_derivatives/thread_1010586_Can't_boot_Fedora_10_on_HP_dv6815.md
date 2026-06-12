---
title: "Can't boot Fedora 10 on HP dv6815"
date: 2008-12-13
forum: Fedora/RedHat and derivatives
---

### Post by 67GTA on 2008-12-13
I decided to give Fedora a try, and can't get it to boot on my laptop. It hangs right after starting cups. It is supposed to go to the login screen at that point, which I assume is graphics related. I've tried several boot options to affect graphics with no luck. I have Nvidia GeForce 7150. I've tried: xforcevesa, vga=791, etc. I did'nt see any "safe mode" options. Can anyone help me get it started?

---

### Post by igknighted on 2008-12-15
Add the number 3 to the end fo the string of boot options to try booting to runlevel 3 (full multi-user, no X).  If that works it probably is graphics related.  Then login as root and run 'Xorg -configure' to generate an xorg.conf (will appear in /root as xorg.conf.new).  Then change the graphics driver to vesa and any other changes you may want and save the file in /etc/X11/ as xorg.conf, and run the command 'init 5' to start up full multi-user + X.

If booting to runlevel 3 fails, check your CD/iso image to make sure it wasn't corrupted.

---

### Post by 67GTA on 2008-12-15
I checked the md5 sum. It boots okay on my HP desktop. The nv driver doesn't support my laptop card yet, so I'm guessing it is graphics related. I had the same problem with Ubuntu, but I got the bulletproofx dialog. I wasn't sure of any of the Fedora boot options. I'll give that a try.

---

### Post by 67GTA on 2008-12-15
That done the trick! I am writing this from the Fedora live CD. For some weird reason it had 16 entries in xorg.conf. It almost looked like it tried to configure every PCI slot as a graphics card. Once I got booted into the desktop, lspci detected everything correctly, and my atheros ar5007 works out of the box. I've never seen anything like that happen before. Does Fedora have an alternate installer like Ubuntu?

---

### Post by igknighted on 2008-12-16
> **67GTA said:**
> That done the trick! I am writing this from the Fedora live CD. For some weird reason it had 16 entries in xorg.conf. It almost looked like it tried to configure every PCI slot as a graphics card. Once I got booted into the desktop, lspci detected everything correctly, and my atheros ar5007 works out of the box. I've never seen anything like that happen before. Does Fedora have an alternate installer like Ubuntu?

There's the DVD, which is similar.  Aside from downloading 4+ gigs worth...  It configures network interfaces not to use network manager by default (which I guess ubuntu's does too?) and a few other things that are annoying for desktop use, so the liveCD is usually preferable.

I'm sure there is a boot option that could fix the PCI issue, but I haven't the slightest idea what it is.

---

