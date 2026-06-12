---
title: "Geforce 210 + NVIDIA drivers"
date: 2010-07-08
forum: Desktop Environments
---

### Post by mhouston100 on 2010-07-08
*Sigh* I've been sepending way to much time trying to get this setup so I thought I might dump the whole lot here and see if anyone has some suggestions.

I've replaced the integrated ATI gfx in my HTPC with a Geforce 210 (to take advantage of VDPAU) and I have been having trouble getting it working without GDM installed.  

Basically, I installed a minimal lucid installation, followed the setup here:

[http://forum.xbmc.org/showthread.php?t=72940]("http://forum.xbmc.org/showthread.php?t=72940")

And everythinig was working fine except for the display.  It jsut would not load the NVIDIA driver module.  So I removed it and installed the latest binary from the NVIDIA site.  Same issue, on boot it fails to load the NVIDIA module. (So it cant load XBMC obviously)

So I do a full desktop install of 10.04, everything working fine, install the latest binary again, SEEMS to be working fine.  Can load XBMC from the desktop, VDPAU seems to be working (judging from CPU usage) and everything is sweet.

I then installed the XBMC-standalone / live package which uninstalls GDM.  Once again the NVIDIA driver fails to load and I can't get a display.  I cant even get a local tty, I can only SSH into the system.

However, simply re-installing GDM goes back to perfectly working!

Last night I did a minimal server install to start from scratch.  Same issue.

It doesnt seem to be a problem with the XBMC install as it reports that no screens found and the NVIDIA module still does not seem to be loaded.

I've blacklist all the other display drivers, uninstalled them, tried countless xorg.conf files all to no avail.

Anyone got any ideas?  

It clearly work as it works as a desktop flawlessly.

Thanks in advance

(btw I have followed nearly every thread in here to get it to work without GDM but no good)

---

### Post by Robyr on 2010-07-10
Why not leave GDM installed and just set up an automatic login? Also, I have a friend who just bought a G210 based card, are you stating that the NVIDIA binary drivers do, indeed, work with this card?

---

