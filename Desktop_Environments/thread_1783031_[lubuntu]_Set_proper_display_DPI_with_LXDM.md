---
title: "[lubuntu] Set proper display DPI with LXDM"
date: 2011-06-15
forum: Desktop Environments
---

### Post by SpaceCat3000 on 2011-06-15
**Problem:**
My laptop incorrectly recognises screen DPI (or PPI, whatever).
Fonts look way to small and antialiasing is not applied as intened.

**Todo:**
Manually set DPI for Xorg (not just font DPI).
My correct value is 118x118 dpi.

**Failed methods:**
Providing */etc/X11/xorg.conf*  OR * /usr/share/X11/xorg.conf.d/60-monitor.conf*  files with options like (none helped):
```

Section "Monitor"
    Identifier "Monitor0"
    DisplaySize 272 204
    Option "DPI" "118 x 118"
EndSection

```Editing */etc/X11/xinit/xserverrc *to contain line like (strange, but did not help):
```
exec /usr/bin/X -dpi 118 -nolisten tcp "$@"
```
**The things that worked:**
Firstly straightforward method of uncomenting */etc/alternatives/lxdm.conf* file to override server args like:
```
arg=/usr/bin/X -nr vt07 -dpi 118 -nolisten tcp
```

did not help as well,
but after some debugging the solution was found in putting arg value within double quotes, like follows:
```
arg=**[COLOR=Red]"[/COLOR]**/usr/bin/X -nr vt07 -dpi 118 -nolisten tcp**[COLOR=Red]"[/COLOR]**
```[B]

Alternative solution (found in Archlinux wiki):[/B]
Run command
```
xrandr --dpi 118
```And place this string in appropriate startup script (like /etc/xdg/Lubuntu/autostart for Lubuntu) if You like this solution.

---

