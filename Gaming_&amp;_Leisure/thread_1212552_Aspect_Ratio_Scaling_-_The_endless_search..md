---
title: "Aspect Ratio Scaling - The endless search."
date: 2009-07-13
forum: Gaming &amp; Leisure
---

### Post by shyce on 2009-07-13
I've always steered clear of using any linux distro on a main rig, simply because I've never been too keen on the troubleshooting & differing installation methods. Recently however, I've needed a quick-install distro so I've turned to ubuntu to host my @home server for website design.

I play Diablo II, Warcraft III, and Starcraft as well during down-time and I've found with these old games that I actually like the aspect ratio to be scaled to fit the screen. 

Now for some specs..
I'm running a [Sony VGN-FZ240E/B]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.docs.sony.com%2Frelease%2Fspecs%2FVGNFZ240EB_mksp.pdf&ei=Qt1bSu_gI8vvlAeKxrTeDA&usg=AFQjCNGmDaLnZ2xI0_IMGr_RIbEy0yBlRQ") Laptop with a GMA965 Intel Chipset (x3100). Currently, my Ubuntu 9.04 (Jaunty) install is fully up-to-date. I've played around with my /etc/X11/xorg.conf file using some other posts I've found around the web but I'm completely stuck.

I can't get games or even none-native ratios to scale and fit the screen. I've searched endlessly on both Google & Bing and I'm turning to the community for help, please any input?

---

### Post by Finalfantasykid on 2009-07-13
Ignore this...  I didn't read that you have an intel graphics accelerator...

```
sudo apt-get nvidia-settings
```Do you have this?  You should be able to Change the scaling options in there...

---

### Post by shyce on 2009-07-13
It's an intel chipset. Will that still work?
(Intel X3100 Integrated graphics, not Nvidia or ATI)

---

### Post by Finalfantasykid on 2009-07-13
No I'm an idiot.  I didn't realize you were using an intel chip.

---

### Post by shyce on 2009-07-14
Any ideas?

---

### Post by del_diablo on 2009-07-14
Running in window modus? I guess......... I got no idea.
Maybe checking your BIOS, some got scaling options.

---

### Post by shyce on 2009-07-14
For any future searchers:

[http://www.svenswrapper.de/english/index.html](http://www.svenswrapper.de/english/index.html)

This enables 3DFX Glide and special features to make Diablo II run amazing in 3d mode and supports pixel aspect ratio scaling. You just copy the files in the zip to the Diablo II directory then set the settings in the exe and run the VidTest. Everything works perfectly now.

---

### Post by BoyOfDestiny on 2009-07-15
If you check the intel manpage, go to Applications -> Accessories -> Terminal)
```
man intel
```
You'll find these options:
[quote=intel manpage]PANEL_FITTING - control LCD panel fitting

By default, the driver will attempt to upscale resolutions smaller than the  LCD&#8217;s  native size while preserving the aspect ratio.  Other modes are available however:

       center

       Simply center the image on-screen, without scaling.

       full_aspect

       The default mode.  Try to upscale the image to the screen  size,  while preserving  aspect  ratio.  May result in letterboxing or pillar-boxing with some resolutions.

       full

       Upscale the image to the native screen size without  regard  to  aspect ratio.   In  this  mode,  the full screen image may appear distorted in some resolutions.
[/quote]

I'm guessing you want "full", although that would cause "stretching".

So in terminal, paste this, then hit enter
```
xrandr --output LVDS --set PANEL_FITTING full
```

Hopefully that's that (and yes I just googled to find that command)

---

### Post by shyce on 2009-07-15
While I thank you for finding that solution, I also assure you that I spent multiple hours searching google without any luck. That last comment was not really needed.

---

