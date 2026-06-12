---
title: "screen res messed up, xorg pastebinned. just need fixin"
date: 2009-01-07
forum: General Help
---

### Post by Cew27 on 2009-01-07
hey guys been on the phone to my dad who's pcs res has recently gone fubar when he used a new monitor (hp 1024X768) here is his xorg which states he has a dell 2408wfp which is a 24 inch beast and certainly not his screen. 
[http://pastebin.com/m12eadbb8](http://pastebin.com/m12eadbb8)
if anyone could fix this i would be more than happy 
thanks alot

---

### Post by Meson on 2009-01-07
With the later versions of X.org, you don't need such a complicated xorg.conf file.  Especially for one monitor.  Try this:

```

Section "Monitor"
    Identifier     "Monitor0"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Option         "NvAGP" "1"  # this line fixes suspend with nvidia cards
    Screen          0
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    # Option         "UseDisplayDevice" "DFP-1"  # this line will let you choose which port to use, for my laptop DFP-0 is the built in, DFP-1 is the DVI, and CRT-0 is the VGA
    DefaultDepth    24 
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by phisher1 on 2009-01-07
Can you explain fubar? Does the GUI load? Is it unreadable? 

A couple solutions..

rm -f /etc/X11/xorg.conf, restart Xorg.. it'll use default settings

or

/etc/init.d/gdm stop, log in at a console, Xorg -configure
then Xorg -config /root/xorg.conf.new

if Xorg works properly, then cp /root/xorg.conf.new /etc/X11/xorg.conf

or

dpkg-reconfigure xserver-xorg

---

### Post by Cew27 on 2009-01-07
put that where? replace the monitor section with it?

---

### Post by Cew27 on 2009-01-07
for the record i have already tried xorg -configure and the screen res is still huge

---

### Post by Meson on 2009-01-07
> **Cew27 said:**
> put that where? replace the monitor section with it?

Yeah replace your monitor, screen, and device sections with the one I gave you.

You can also add to your device section:
```

option metamodes "nvidia-auto-select"

```

---

