---
title: "2nd Monitor, propr. ATI drivers - again"
date: 2009-03-26
forum: Desktop Environments
---

### Post by JackH79 on 2009-03-26
Hello everyone,
very happy so far to have made the switch to Linux and to have found this forum.

Problem is: After having spent a few days fiddeling with all the settings and some drivers everything works perfectly fine on my laptop - except my external monitor which I'm using at home. Thing is, that I don't want or need a clone or 'big desktop' setup. All I want is for the computer to switch to my big Monitor (22" @ 1680x1050) and to run under the max. resolution whenever I plug it in and to turn off my laptop screen (1280x800) and vice versa when I take it out again.
Now, that trick works perfectly fine under Vista and even under Ubuntu (8.10) when I use the original graphics driver Ubuntu shipps with - so I know that my system can handle it. But in order to use the 3D capabilities of my graphics card I need to switch to the proprietary driver. They work perfectly fine, except for that monitor switching thing. I can clone (or extend) the desktop (using Catalyst Control Centre) on to it but only at 1280x800, which cuts off half of it and leaves a pretty grainy picture, or uses only half of my screen.

I tried to fiddle around with the xorg.conf and the aticonfig but apparently I'm too stupid to understand the workings.
Now, I know that this kind of question has been asked a million times before and I apologise in advance, but even after browsing through the web for days and following all sorts of advice and after getting my twentieth black screen at start-up I thought I just give up and ask the experts for help. I'd be grateful for any advice (or just tell me that it's not possible and can stop worrying about it). Thanks for reading and thanks in advance for any hints.
Cheers
Jack

PS: My current xorg.conf:

```
Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
EndSection

Section "Module"
Load "glx"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
EndSection
```

(The overlay options don't have any influence, just need them to run smooth videos.)

My details:
Laptop Acer Aspire 5710
Intel Core Duo @ 2 GHz
Mobility Radeon HD 2300
4 Gig DDR2 Ram (though Ubuntu recognises only 3, similar to Vista without SP1)
Ubuntu 8.10

---

