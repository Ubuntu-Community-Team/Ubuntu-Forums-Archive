---
title: "Font rendering broken in Hardy"
date: 2008-05-12
forum: Desktop Environments
---

### Post by dmik on 2008-05-12
After upgrading from Gutsy to Hardy, I noticed that font rendering is no more consistent across gnome-terminal, Qt3/Qt4 apps and all other GTK apps.

See is the attached screenshot to get what I mean. Here are some comments:

[LIST=1]
[*]All text "Quick Brown Fox..." is written using DejaVu Sans Mono 10pt everywhere.
[*]All GTK apps render fonts perfectly as before (e.g. as in Gutsy).
[*]Qt3/Qt4 apps obviously use a different rasterizer. You can see that anti-aliasing is more "dirty" and "noisy" and hinting doesn't work properly for DejaVu Sans (look at the poor Qt3/Qt4 dialog font)
[*]The gnome-terminal's font is bigger than it should be and anti-aliasing is more "dirty" and "noisy" (compare to gedit).
[/LIST]

If it's important, I have the ATI Mobility Radeon 9600 video and use the latest (installed by Hardy) binary driver from ATI.

DPI is set to 96 everywhere (checked using xdpyinfo, xrdb, gconftool --get /desktop/gnome/font_rendering/dpi).

In Gutsy, all four examples above would show the identical size and shape of DeajVu Sans Mono (and other fonts), which looked like in gedit. (I'm not 100% sure about anti-aliasing in Qt, but 100% sure about gnome-terminal).

Is there any chance to get identical font rendering everywhere?

---

