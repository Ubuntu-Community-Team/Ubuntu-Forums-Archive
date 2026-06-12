---
title: "Fallback indicator CSS styles?"
date: 2012-04-27
forum: Desktop Environments
---

### Post by LarsKongo on 2012-04-27
I'm trying to style the indicator applet in Gnome Fallback in Ubuntu 12.04.

The text in my normal gtk .menubar is dark colored and my gnome-panel has a dark background. I've tried changing everything in the gnome-panel.css file to:
*color: @dark_fg_color;*
But nothing seems to work.

I suppose the indicator applet must have some CSS name that allows me to change it, but I can't seem to figure it out. I've tried:
```
IndicatorApplet,
IndicatorAppletComplete,
IndicatorAppletCompleteFactory,
*Indiciator* { color: @dark_fg_color; }
```
Nothing of that is working.

I wish I had something like gtkparasite that was really useful for gtk2 apps. :(

---

### Post by bogan on 2012-04-28
**Hi**!  I think the names you tried should have hyphen '-' separators, and be in lower case, eg.' indicator-applet'.  

Chao!, **bogan**.

---

