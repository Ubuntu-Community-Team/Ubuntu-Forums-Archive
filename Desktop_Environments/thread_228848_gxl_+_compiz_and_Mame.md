---
title: "gxl + compiz and Mame"
date: 2006-08-03
forum: Desktop Environments
---

### Post by amoore on 2006-08-03
When I try to run Mame with gxl + Compiz in full screen mode the Gnome task bar and menu bar do not disappear and are left up during game play. When I run Mame without  gxl + Compiz the Gnome task bar and menu bar do disappear. 

The front ends that I'm using for Mame are GXMame and KXMame.

Any suggestions?

---

### Post by r3dux on 2006-08-18
Amoore, I've noticed the same thing with KDE (the panel gets left on the bottom), but I found that if you right click the panel and go Panel Configuration | Hiding then select "Allow other windows to cover the panel" xmame will go fullscreen in xgl without issues. 

This does then mean that other windows (firefox, whatever) can also cover the panel, so you might want to just add a hiding button to it and hide the panel before you play anything, leaving you with just the small hide button instead of the full thing. It's a bit of a dirty-hack, but it works for now!

Strangely enough, running "xmame -video-mode 2 -fullscreen <somegame>" outside of Xgl fullscreens it in gl mode perfectly without having to do *anything* to the panel at all, so there's bound to be a way...

If you find it, plz post back!

Kind regards,
r3dux

---

