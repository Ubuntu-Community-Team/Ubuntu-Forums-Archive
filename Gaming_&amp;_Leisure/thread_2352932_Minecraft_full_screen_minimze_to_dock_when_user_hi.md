---
title: "Minecraft full screen minimze to dock when user hit alt key."
date: 2017-02-17
forum: Gaming &amp; Leisure
---

### Post by lt_gustavsen on 2017-02-17
Hello. My son sometimes hit the left alt button when he play minecraft. This is on fresh vanilla ubuntu 16.04 64bit. If minecraft is in fullscreen it will minimize to dock. 
I have done some searching and have disabled the alt HUD function.
```
$gsettings get org.compiz.integrated show-hud 
['']
$
```

But that don't help in minecraft. 

I also tried to install the mate desktop via apt, and in that environment alt key don't mess with minecraft, so it works well. 
Any clues what I can do in ubuntu unity?

---

### Post by efflandt on 2017-02-18
You might try installing CompizConfigSettingsManager. In that have a look at **Ubuntu Unity Plugin**

The only things (2) that I see right off the bat for **Alt** key are:
- Key to show the menu bar while pressed
- *Key to show the HUD when tapped* (in italics)

Maybe it is the latter, which you could either set as **Disabled**, for either or both of those, or assign some other key.

I had an issue with my Logitech MX Master mouse which has a hidden button below my thumb which would send Ctrl+Alt+Tab, which would switch windows (or to desktop). That was quite annoying when that would happen in the middle of an intense on-line game. So I used Ubuntu Unity Plugin settings in CompizConfigSettingsManager to change the key combination for "Key to start the Switcher for all viewports" from <Control><Alt>Tab to <Control><Alt><Home> and that eliminated my window switching problem.

---

### Post by lt_gustavsen on 2017-02-19
> **efflandt said:**
> You might try installing CompizConfigSettingsManager. In that have a look at **Ubuntu Unity Plugin**

The only things (2) that I see right off the bat for **Alt** key are:
- Key to show the menu bar while pressed


Thank I missed that setting.

---

