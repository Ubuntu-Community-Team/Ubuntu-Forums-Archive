---
title: "SVG Wallpaper"
date: 2005-02-28
forum: Desktop Environments
---

### Post by bobmitch on 2005-02-28
I am messing around with SVG wallpapers right now, but it seems that the gnome rasterizer somehow looks at a screen width rather than the xserver width (virtual or otherwise) to determine the resolution of the final image.

I am running on a "large desktop" style ati 9800 dual monitor setup at 2560 x 1024, but it appears (to my eyes) that if I choose to 'fill display' option in the wallpaper settings, the svg is rendered to a 1280x1024 bitmap, then stretched - thus defeating the beauty of an svg file.

I would have liked that 'fill display' would do exactly that, fill the display, stretching and distorting the svg output as necessary, and that the 'centered' option would fill the entire display whilst maintaining the correct aspect ratio.

Is this a bug, or a design decision?  Can the ubuntu/gnome developers shed any light on this?

Rgds,
mitch

---

### Post by valadil on 2005-02-28
As far as I can tell, the width that various windows use is determined by your window manager.   I too use two 1280x960 screens.  In my experience, xfwm is pretty good about maximizing correctly.  Metacity is decent, and sawfish just doesn't do it at all.  Changing wms may actually help with this problem, since at some level Nautilus (the thing that manages your icons and draws your wallpaper in gnome) is a fullscreened window.

---

