---
title: "difference between --orientation and --rotate of xrandr?"
date: 2021-11-23
forum: Desktop Environments
---

### Post by seung-hs on 2021-11-23
[COLOR=#1A1A1B]hi.
Status)
I'm using vertical monitor, so I have to rotate the screen.
So I used this comand.> xrandr -o left

But someday, it changed. So this command works as I intend.
> [COLOR=#1A1A1B]xrandr -o normal[/COLOR]

Strangely, `[/COLOR][COLOR=#0000ff]xrandr --output HDMI-0 --rotate left[/COLOR][COLOR=#1A1A1B]` result is same with `[/COLOR][COLOR=#0000ff]xrandr -o normal[/COLOR][COLOR=#1A1A1B]`

Linux ver: Ubuntu 20.04 Desktop


Question)

What's difference between --orientation and --rotate of xrandr?
And why the orientation is changed without any settings?



If you know about xrandr, please help me.

[/COLOR]

---

### Post by Holger_Gehrke on 2021-11-23
'--orientation' is an old - RandR 1.1 - option which doesn't need a specified '--output' (it is so old that at the time having multiple displays connected to the same machine was an unheard of luxury; I think this version of RandR predates Linux by a few years ...). On my system - laptop with external display, the external set as default display, internal as secondary (and often switched off) - using '--orientation' with an '--output' option will do exactly nothing no matter which output I specify. Without the '--output' it will rotate the default output and switch the other output off.

'--rotate' on the other hand is a newer option (RandR 1.2) and does need an output and will only rotate the given output and leave any other outputs alone.

Another thing to think about: xrandr is for X11. If you're using Wayland xrandr will probably not work.

Holger

---

