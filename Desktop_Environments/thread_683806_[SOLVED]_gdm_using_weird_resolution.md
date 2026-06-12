---
title: "[SOLVED] gdm using weird resolution"
date: 2008-01-31
forum: Desktop Environments
---

### Post by emanuel.landeholm on 2008-01-31
For some reason gdm starts X in 1152x768. When I log in to gnome I get 1280x1024 @85Hz.
If I comment out the HorizSync & VertRefresh lines in the Monitor section of my xorg.conf
gdm uses 1280x1024, but gnome will only allow 60 Hz in 1280x1024. I just don't understand why
X behaves differently. Is gnome or gdm using some other config that I don't know about?

I have an ADI MicroScan 937G CRT monitor connected to one of the two VGA outputs of my
Radeon 9600 AGP card. When I switch output X fails to start complaining that both VGA outputs
are disconnected, but windows XP works with both outputs.

I'm using the open source drivers from xorg. I have the same problem in gentoo and ubuntu gutsy
with slightly different xorg.confs and driver versions.

cheers

---

### Post by overdrank on 2008-01-31
> **emanuel.landeholm said:**
> For some reason gdm starts X in 1152x768. When I log in to gnome I get 1280x1024 @85Hz.
If I comment out the HorizSync & VertRefresh lines in the Monitor section of my xorg.conf
gdm uses 1280x1024, but gnome will only allow 60 Hz in 1280x1024. I just don't understand why
X behaves differently. Is gnome or gdm using some other config that I don't know about?

I have an ADI MicroScan 937G CRT monitor connected to one of the two VGA outputs of my
Radeon 9600 AGP card. When I switch output X fails to start complaining that both VGA outputs
are disconnected, but windows XP works with both outputs.

I'm using the open source drivers from xorg. I have the same problem in gentoo and ubuntu gutsy
with slightly different xorg.confs and driver versions.

cheers

HI and I am a little confused about your xorg. 
```
[COLOR="Red"][COLOR="Red"]Section "Device"
        Identifier      "ATI Technologies Inc RV350 AP [Radeon 9600]"
        Driver          "radeon"
        Option          "XAANoOffscreenPixmaps" "true"
        Option          "AGPMode"        "8"[/COLOR][/COLOR]
#
# FastWrite hard hangs, disabled
#
#       Option          "AGPFastWrite"   "on"
        Option          "AccelMethod"    "XAA"  #either XAA or EXA. only "XAA" is supported for some of the cards with "experimental" 3d acceleration
        Option          "ColorTiling"    "on"
#
# EnablePageFlip only works with XAA.
# [Incompatible with tuxonice, so disabled]
#
        Option          "EnablePageFlip" "on"
        Option          "DMAForXv"       "true" #This can speed up movie playback but can in rare cases case instability
        Option          "GARTSize"       "64"   #This is the size of the "GART" that xorg will use.
        BusID           "PCI:1:0:0"
EndSection

[COLOR="Red"]Section "Device"
        Identifier      "Vesa"
        Driver          "vesa"[/COLOR]

        BusID           "PCI:1:0:0"
EndSection

```
I have highlighted the questions. You have two devices listed with two different drivers. Have you tried removing one and also have you tried using the fglrx drivers?

---

### Post by emanuel.landeholm on 2008-02-01
Problem solved, see [http://forums.gentoo.org/viewtopic-t-653939.html]("http://forums.gentoo.org/viewtopic-t-653939.html").

> **overdrank said:**
> HI and I am a little confused about your xorg. You have two devices listed with two different drivers. Have you tried removing one and also have you tried using the fglrx drivers?

You may specify as many devices as you like. Just select the active one(s) in your Screen section. I did try using fglrx but it was too flaky so I decided to go with the xorg driver instead. Maybe I should check it out again.

---

