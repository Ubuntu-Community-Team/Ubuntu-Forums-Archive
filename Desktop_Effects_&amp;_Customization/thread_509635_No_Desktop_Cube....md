---
title: "No Desktop Cube..."
date: 2007-07-25
forum: Desktop Effects &amp; Customization
---

### Post by Pablo Pablovski on 2007-07-25
Ok, I've had a working Beryl desktop for a while, and installed Compiz-Fusion to try it out. I had some problems with it, so went back to dear ol' Beryl (lovely girl). Now, I don't get a working cube - can't rotate or move windows between desktops.

When I run "Beryl-Manager", I get errors, below. The splash appears and most Beryl feature work, but no cube.

WhadidIdo? Any ideas, chaps and chapesses?


beryl: Plugin 'cube' can't be activated because plugin 'plane' is already providing feature 'largedesktop'
Couldn't initialize cube. This should not happen!
beryl: Plugin 'fadeDesktop' can't be activated because plugin 'showdesktop' is already providing feature 'showdesktop'
Couldn't initialize fadeDesktop. This should not happen!
beryl: 'rotate' plugin needs feature 'cube' which is currently not provided by any plugin
beryl: Can't activate 'rotate' plugin due to dependency problems
Couldn't initialize rotate. This should not happen!

---

### Post by tnseditor on 2007-07-26
Try going into System-->Preferences-->CompizConfig Setting Manager.  You first have to disable the "desktop wall" and "desktop plane".  After those are disabled try to enable "desktop cube" and "rotate cube".  You may need to hit ALT-F2 and type "compiz --replace" to get it to work.  By the way, the cube is no longer activated by the center mouse button, but by   Control+Alt+left mouse button.

---

