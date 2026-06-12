---
title: "Optiplex GX260 and direct rendering"
date: 2007-07-01
forum: Dell  Ubuntu Support
---

### Post by rrinker on 2007-07-01
I am running 7.04 on an Optiplex GX260 slimline desktop. Using the embedded 845 video, I can;t get direct rending to work.  I DO have the A09 BIOS, and set the video memory to 8MB (from the default of 1MB), and I had no problems installing Ubuntu. X was using the VESA driver until I changed it to the i810, and with a little tweaking based on other threads here and managed to get glxgears to over 830fps. Tuxcart and Planet Penguin Racer are playable so I guess I can;t complain too much, but reading other threads it seems that others with the same machine have been able to get the direct rendering to work. I don;t want to mess with things too much (already had to boot to console and replace xorg.conf with my backup a few times) since everything else I'm running on this machine is working extremely well, but if there are any additional hints as to what I can try, I'd love to ehar them. I suspect it's NEVER going to actually work since there's only 8MB video memory and no way in the hardware/bios to make it use more.

                                                     --Randy

---

### Post by angryfirelord on 2007-07-13
Install this package: xserver-xorg-video-intel

Then, go into your xorg.conf file and change the driver to day "intel".

---

### Post by rrinker on 2007-07-31
I finally got it fixed! A little random Googling and I found some references to the GX260 with other flavors of Linux. The trick it seems it to make sure the following three things are set in the BIOS:

 Video Memory to 8MB
 AGP Aperature to 256
 DAC Palette Snoop ON

I rebooted and with no other changes (I already had it loading the i810 driver in xorg.conf) I get direct rendering: yes in glxinfo, and over 700 fps in glxgears. Planet Penguin Racer is playable at 1280x1024 even.

 Who would figure, palette snoop - the one thing you NEVER EVER want to turn on for Windows.

Not bad for a somewhat outdated (but free - I got it from a client) computer. 

              --Randy

---

