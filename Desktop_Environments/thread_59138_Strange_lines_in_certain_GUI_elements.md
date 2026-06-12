---
title: "Strange lines in certain GUI elements"
date: 2005-08-22
forum: Desktop Environments
---

### Post by fpoole on 2005-08-22
Hello!

I'm running Kubuntu a Dell Latitude CSx laptop. The video card is a NeoMagic NM2360 [MagicMedia 256ZX] (according to xorg.conf). For some reason, certain window decorations, the Konqueror background, and some widgets have vertical blue-or-white lines running down them in patterns. I've tried reconfiguring X once and ended up reverting to my old xorg.conf after a bit of a nasty crash.

This is quite annoying (and beyond ugly), so any help is appreciated! ;)

/fpoole_

---

### Post by mindspin on 2005-08-23
Hi, same here on a thinkpad 600x, also neomagic.

I solved it partially by playing around with using window settings "laptop", and style "plastic" instead of ceramique but its not satisfying me completely.

---

### Post by Lord Illidan on 2005-08-23
Try modifying the xorg.conf and change the driver to "vesa"

---

### Post by skoal on 2005-08-23
Are you using the "neomagic" driver in xorg.conf?
```
Section "Device"
[...]
        Driver          "[COLOR=DarkRed]neomagic[/COLOR]"
[...]
        Option "NoAccel" "false"
        Option "OverlayMem" "829440"
        Option "XaaNoOffscreenPixmaps"
        Option "XaaNoScanlineImageWriteRect"
        Option "XaaNoScanlineCPUToScreenColorExpandFill" 
EndSection
```
You can also try to add several (or any) of the options listed as well.  I believe most of those options aren't related to your case, but necessary for proper DVD playback and such on some of those chipsets.

change the color depth from 24 to 16 or vice-a-versa:
```
Section "Screen"
        Identifier      "Default Screen"
[...]
        Monitor         "Generic Monitor"
        DefaultDepth    [COLOR=DarkRed]16[/COLOR]
EndSection

```
Make one chane at a time, logout, kill (restart) X server with ctrl-alt-backspace, log back in, and note any "improvements" (if at all)...

\\//_

---

### Post by fpoole on 2005-08-23
[QUOTE=Lord Illidan]Try modifying the xorg.conf and change the driver to "vesa"[/QUOTE]

Thanks! That did it. ;)

I'll look at some of the other suggestions posted too. Thanks for the help.

---

