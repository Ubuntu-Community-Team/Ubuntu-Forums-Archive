---
title: "Different Backrounds for Dual monitors? Moving windows between them?"
date: 2005-11-06
forum: Desktop Environments
---

### Post by Kamir on 2005-11-06
Hi there,

I finally managed to extend my desktop on 2 montiors with the resolutions i want to. 
Now i wonder, wether its possible to put two different Backrounds on both screens or to use an extended backround over both, as it works in windows.

2nd, i would love to be able to move windows from one destop to the other, is that possible or not?

plain "no"s would help me a lot allready, then i could stop searching in the net :)
thnx for any feedback

---

### Post by dvejnovic on 2005-11-06
You can:
- right click with mouse on desktop (all other window are closed or minimized)
- select "Configure desktop" from dropdown menu
- configure your desktop...:cool:

---

### Post by Leif on 2005-11-06
you can drag and drop windows from one screen to the other just fine. the background issue is a bit more tricky. if you've got a background that's the right size for the combined area, it'll stretch. if you want a separate picture on each screen, then you need to fire up gimp and combine the two pictures manually.

---

### Post by Kamir on 2005-11-06
that will result in a clone-backround for both monitors... thats not what i mean

i want an 2560x1024 backround extending on both monitors! 
it just looks so much cooler :cool:

and for leif: if i put the 2560x1024 backround on, it wont stretch on both, it will shrink down on each monitor :(
even the windows moving doesnt work, it wont let me, i can only move the mouse alone into the other screen... grmbl maybe i did something wrong with my xorg.conf ...

---

### Post by Leif on 2005-11-06
[QUOTE=Kamir]
and for leif: if i put the 2560x1024 backround on, it wont stretch on both, it will shrink down on each monitor :(
even the windows moving doesnt work, it wont let me, i can only move the mouse alone into the other screen... grmbl maybe i did something wrong with my xorg.conf ...[/QUOTE]

can you post your xorg.conf, because it doesn't sound right that you can't move things around.

---

### Post by Kamir on 2005-11-06
here it is, it was quite some work to get the second monitor working with 1280x1024 as the system didnt recognize the monitor. for some reason it only works with this setting.
now i have practically 2 desktops on their own, which i can use with one mouse and keyboard. all bars are on both destkops(unlike windows) and everything opens on the desktop where i click on it

```

Section "Module"
	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "Device"
	Identifier  "TFT ATI Graphics Adapter 0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      0
EndSection

Section "Device"
	Identifier  "TFT2 ATI Graphics Adapter 0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
	Option      "IgnoreEDID" "True"
EndSection

Section "Monitor"
  Identifier    "TFT"
  Option        "DPMS"
  HorizSync	64
  VertRefresh	60
  DisplaySize   376 301
EndSection

Section "Monitor"
  Identifier    "TFT2"
  Option        "DPMS"
  HorizSync	64
  VertRefresh	60
  DisplaySize   376 301
EndSection


Section "Screen"
  Identifier    "TFT"
  Device        "TFT ATI Graphics Adapter 0"
  Monitor       "TFT"
  DefaultDepth  24
  SubSection    "Display"
     Depth        24
     Modes        "1280x1024"
  EndSubSection
EndSection

Section "Screen"
  Identifier    "TFT2"
  Device        "TFT2 ATI Graphics Adapter 0"
  Monitor       "TFT2"
  DefaultDepth  24
  SubSection    "Display"
     	Depth     24
	Modes	  "1280x1024"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier   "Default Layout"
  Screen 0 "TFT" 0 0
  Screen 1 "TFT2" LeftOf "TFT"

  InputDevice   "Generic Keyboard"
  InputDevice   "Configured Mouse"
EndSection

Section "DRI"
	Mode         0666
EndSection

```

---

### Post by ranf on 2005-11-06
[QUOTE=Kamir]
now i have practically 2 desktops on their own, which i can use with one mouse and keyboard. all bars are on both destkops(unlike windows) and everything opens on the desktop where i click on it
[/QUOTE]
Looks like Xinerama is what you want. Add these lines to your xorg.conf:
```
Section "ServerFlags"
        Option  "Xinerama"      "True"
EndSection

```

---

### Post by Kamir on 2005-11-08
As always, when you try something another problem comes up!
I added Xinerama:

Section "ServerFlags"
        Option  "Xinerama"      "True"
EndSection

and now my desktop is messed up in a way hard to describe, i can work with the primary screen well but graphical errors will com eup, when i try to use the other one. 
another important point, my system wont load my fglrx driver anymore, instead put up those old mesa ones, i had before... 
if i put it off again, i ends up with a different session on each monitor again.

I couldn't find anything how Xinerama affects the system or how to configure it :(

---

### Post by RawMustard on 2005-11-08
This page helped me out immensely.  Although I have an nvidia card, I'm sure the ATI would work just as well following the ATI instrucions :)

[http://gentoo-wiki.com/HOWTO_Dual_Monitors#ATI](http://gentoo-wiki.com/HOWTO_Dual_Monitors#ATI)

---

