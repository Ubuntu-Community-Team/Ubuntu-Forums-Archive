---
title: "Desktop effects causing window drawing problems"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by niallporter on 2007-04-22
hi all,

I just did a clean x86 install of Feisty Fawn on my girlfriend's desktop yesterday.  It's a Dell Dimension 5000 (non-64bit P4, ATI X300 gfx, 512MB RAM) and all seemed to work fine at first.  When I enabled the desktop effects for her it seemed to work fine until the next time I rebooted.

After a reboot whenever she opens any application it doesn't draw properly.  She can see the window and areas where there are meant to be scrollbars (in grey) and text display/input areas (in white) but nothing more to start with unless she resizes the window slightly, this seems to force it to draw the window contents properly.  Also, any text typed doesn't appear until after she has hit the enter key.  This happens in any application we've tried, the terminal, Firefox, aMSN, GAIM, whatever.

I haven't installed the official ATI drivers as I had no end of problems with them on my own Fedora box so we're just using the standard open-source ATI drivers and xorg.  The only change I made was to run "dpkg-reconfigure -phigh xserver-xorg" as root and selected "1280x768" as the video resolution as this is the native resolution for her monitor.  Other than that it's a stock install.  Any ideas?

TIA
Niall

---

