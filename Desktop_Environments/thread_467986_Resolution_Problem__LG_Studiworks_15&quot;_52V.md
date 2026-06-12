---
title: "Resolution Problem : LG Studiworks 15&quot; 52V"
date: 2007-06-08
forum: Desktop Environments
---

### Post by robin.rawal on 2007-06-08
Hi. I am a Linux newbie.

I recently installed Ubuntu 7.04 on my system. Intel D945G Motherboard.

I am having some problems with display, .If i select 1024x768, the display is out of screen. Means if i move cursor to the corners, screen scrolls to reveal the remaining part of screen.

LG Studioworks 15" 52V Monitor
Rés Max 1024 x 768 (60Hz)
Dot Pitch 0,28 mm , compatible Plug and Play
Fréq : Horizontal 30 - 54 kHz
Vertical 50 - 120 kHz

If i manually add 1024x768@60hz with this modline.


```
# 1024x768 @ 60Hz,  47.52 kHz hsync
    Mode "1024x768"
    DotClock     57.40
    HTimings  1024 1040 1104 1208
    VTimings  768 770 772 792
EndMode 
```

Then Vertical display is OK, but he horizontal display is out of screen. Any thing that i can try changing in this modline to make it work ???

XP Pro works fine on 1024x768 @60Hz.

I tried everything, reconfigured xorg, manually entered Horizontal sync, vertical refresh, modlines.


please suggest any fix :(

---

