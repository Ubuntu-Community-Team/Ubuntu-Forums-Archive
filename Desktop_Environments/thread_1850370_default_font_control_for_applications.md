---
title: "default font control for applications?"
date: 2011-09-26
forum: Desktop Environments
---

### Post by arsenix on 2011-09-26
I just upgraded to Oneiric beta, and so far most things are working great.  One nagging issue is that for some reason the default fonts have gotten MUCH larger (ie the application drop down menu's, button text etc) which makes most applications look incorrect.  Fonts which are rendered to a specific size by the application (like web pages, html emails etc) are fine.

I am running Xubuntu, but I use Awesome as a window manager.  Consequently I'm not exactly sure where applications pull in the font size.  The DPI setting looks correct.  I have tried changing font settings using the xfce settings panel, as well as gnome-tweaks-tool, and the gnome accessibility panel... but none seem to have an effect.

Anyone have an idea?


James

---

### Post by arsenix on 2011-09-27
I've partially fixed the problem by changing the default font in the gtk theme.  There still seems to be something up with the font sizes though.  I changed the font size to 6pt, which makes them reasonably sized... but they are still way larger than 6pt.  Non-GTK apps still have extremely large fonts.

   Fonts look normal under XFCE session, so it seems to be somehow related to awesome... but definitely something new in Oneiric.  I'll investigate with awesome folks as well. 


James

---

### Post by arsenix on 2011-09-29
I have discovered a better fix.  Launching xfsettingsd causes all apps to be skinned (fonts and all) identical as if running under the xfce session.  This repairs the font sizes in all apps, and also seems to override the gtk/gnome theme settings I was playing with before.

I am unsure if this is really "the fix" or just a bandaid... but at this point this seems to do what I want.


James

---

