---
title: "I cannot set screen resolution"
date: 2007-07-26
forum: Desktop Effects &amp; Customization
---

### Post by nsavigear on 2007-07-26
However much I edit xorg.conf, even to the extent of pasting in one from a known working system, only 800x600 resolution is offered,. Nvidia settings won't let me change anything. The accelerator installed without problems so the screen wobbles nicely. The chipset is Nvidia GFX 5200, monitor CTX PV520, both correctly identified on install. (Maybe a clue - I get exactly the same problem with Sabayon 3.3 and KDE, though Fedora 7 changes resolution quite happily so I know it's not a hardware problem, (but Fedora insists there is no ethernet cable attached!)

I've been two weeks looking for an answer, but nobody has come up with anything that works yet, so there is a challenge!

Otherwise it's back to the "other" OS.

---

### Post by Steve1961 on 2007-07-26
I don't know if this will help, but I have an Nvidia card and use these entries in xorg.conf, and everything works fine:

Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
    Option      "RenderAccel"   "1"
    Option      "AllowGLXWithComposite" "1"
    Option      "RandRRotation" "1"
    Option      "AddARGBGLXVisuals"     "1"
    Option      "DisableGLXRootClipping"        "1"
    Option      "TripleBuffer"  "1"
    Option      "UseEDID"       "1"
    Option      "UseEdidFreqs"  "1"
    Option      "DynamicTwinView"       "0"
    Option      "IgnoreDisplayDevices"  "TV"
    Option      "Coolbits"      "1"
#       Option      "UseEdidDpi"   "FALSE"
    Option      "DPI"   "96 x 96"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection

I can't claim that I know what everything does - I use Kano's Nvidia install script (Kanotix) for my Debian system and these are the entries it inserts.

---

### Post by xc3RnbFO8P on 2007-07-26
As last change, try **Envy** (if you havent) it in Add and Remove.

---

### Post by llln30lll on 2007-07-26
I used ENVY and let it install my drivers \\:D/

---

### Post by nsavigear on 2007-07-26
OK - can you give me a link to ENVY please, I can only find a mention of it in relation to sound cards.

Thanks

---

### Post by xc3RnbFO8P on 2007-07-26
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by nsavigear on 2007-07-27
Thanks.
but
 Envy installed and run. Now I have glorious (and only) 640x480 instead of 800x600! This suggests that since it is probably only the driver that has changed, that must be where the problem lies. I guess I somehow need to find out which driver Fedora was using. (Blast - another install, I'm running out drives).

---

### Post by nsavigear on 2007-07-30
Thanks to all who have tried to help. There are so many inconsistencies here that I'll probably never know what the problem was. I suspect:

A) Failure of install to identify hardware (except Ubuntu gave the correct names, the only install to do so.

B) The ageing monitor not identifying itself ( but see above).

So Fedora installed at the correct resolution but insisted there was no ethernet cable.

Ubuntu would only run at 800x600 until I used Envy, after which it only ran at 6408x480.

At the third fresh install Sabayon is now running at whichever resolution I ask, Beryl is performing all her (admittedly non-productive, but pleasing visual effects, they really impress my Windows friends) and as soon as I can get  the script correct, Thunderbird will be doing what I need. (To avoid multiple e-mail folders it has to be set up to use the established Windows files). I'm a dead man if I suggest my wife transfers to Linux.

Again, many thanks to helpers, I'm now going from Ubuntu to Sabayon.

---

