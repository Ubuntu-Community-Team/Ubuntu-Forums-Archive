---
title: "[SOLVED] Windows load behind gnome-panel"
date: 2008-11-21
forum: Desktop Environments
---

### Post by pirattrev on 2008-11-21
I recently upgraded to **Hardy Heron** after using **Gutsy Gibbon** for a long time. Until a few days ago everything was working fabulously, apart from some irritating sound bugs but that's not the purpose of this thread. In the past day or two, everytime I open a new window, regardless of application (as long as it's handled by _metacity_) the window loads _behind _the _gnome-panel_, at the top of my screen. This wouldn't be so bad but it gets extremely irritating because I like having the gnome-panel on top, and therefore the metacity bar, which I use to drag, close, minimize and maximize windows with ease is stuck behind the panel. To even move the windows I have to Alt-Click to drag them out from behind the panel, which is an extra (although simple) time consuming step [plus friends who use the laptop are constantly stumped and I have to show them the solution time and again]. Any ideas on why this is happening?

---

### Post by pirattrev on 2008-11-21
bump?

---

### Post by pirattrev on 2008-11-22
well, unfortunately no help right away, but I solved my own problem. If anyone has the same situation, and you're running compiz, take a crack at this.  Check to make sure your "Place Windows" feature is turned on. If it isn't and you're running compiz that could be the problem, because when running compiz, it handles the rendering instead of the regular built in engine and treats the gnome-panel like any other thing on the desktop, seeing as compiz doesn't flow perfectly with gnome. So instead it uses it's "Place Windows" function to determine where windows render, so, if turned off, they render in the top left corner (regarded as the first section of the screen) an therefore would render underneath the gnome-panel (if you put it up top). Hope this helps some guy or gal.

---

