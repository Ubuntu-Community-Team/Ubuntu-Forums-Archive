---
title: "Dell Inspiron 2600 video 'i810' driver... xorg.conf"
date: 2009-11-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tetris11 on 2009-11-14
Hey there,
I've been having this problem with my Dell Inspiron 2600 laptop for a while now: I cant get it to work with any of the intel drivers.

I am 100% sure that I have an i830 chipset, which is (apparently) covered by the i810 driver. Only this does not work, and produces a really annoying black flickering effect without actually outputting anything.

So right now Im stuck with vesa. Just like I was with gentoo, sabayon, debian , (list goes on). I thought I'd try Ubuntu again because of its new Dell support, but Im still getting the same problems.

If anybody could shed some light I'd be really really grateful.
Here's the device section of Xorg.conf:
```
Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "ColorKey"                  # <i>
        #Option     "CacheLines"                # <i>
        #Option     "Dac6Bit"                   # [<bool>]
        #Option     "DRI"                       # [<bool>]
        #Option     "NoDDC"                     # [<bool>]
        #Option     "ShowCache"                 # [<bool>]
        #Option     "XvMCSurfaces"              # <i>
        #Option     "PageFlip"                  # [<bool>]
        Identifier  "Card0"
        Driver      "vesa"
        VendorName  "Intel Corporation"
        BoardName   "82830 CGC [Chipset Graphics Controller]"
        BusID       "PCI:0:2:0"
EndSection
```
Btw I've tried the i810 driver with the following options set to "true":
DRI, NoAccel, FBDev

---

### Post by fbergski on 2009-11-14
I'm having the same problem with my Dell 2400 desktop. Stuck in VESA mode.  I don't understand how to load the intel drivers.

Anyone?

Philip

---

### Post by tetris11 on 2009-11-14
Yeah, I feel as if the Linux community has just gone on to bigger and better things, and have just left us forgotten in the dust. 

Fix the damn intel drivers!!! Or at least give us back the XFree86 drivers!

---

### Post by gaming_guy on 2009-11-28
Hi people

i have got debian lenny and ubuntu 8.04 (server with xfce as the gui) working on this laptop. i haven't had much success with 9.10 though.

for debian and 8.04, i used [this method]("http://ubuntuforums.org/showthread.php?t=1011213&page=2") and now have a decent resolution (1024*768).

hope this helps :)

---

