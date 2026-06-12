---
title: "Crystal Fvwm and Thunar"
date: 2007-08-29
forum: Desktop Environments
---

### Post by Ripfox on 2007-08-29
Hi...I cannot seem to get any of these minimal window managers to recognize thunar as the file manager...i have it installed and I thought for SURE fvwm-crystal would recognize it in the menu (as icewm,openbox,fluxbox and blackbox didn't.)

I HATE ROX-FILER :lolflag:

How do I add this to the menu so I do not have to start it from the terminal (I am a newb at fvwm)

Thnx 

Rip

---

### Post by merlinus on 2007-08-30
I run Thunar with fluxbox from the menu.  I added an entry for it.  Very straightforward.

Post back if you would like assistance in setting this up.

-merlin

---

### Post by Ripfox on 2007-08-30
Yes, I have no idea how to make this show up in the menu.

Thanks

Rip

---

### Post by merlinus on 2007-08-30
.fluxbox/menu

At the top, after the line that says:

[begin] (Fluxbox) {} <>

Add:

[exec] (Thunar) {/usr/bin/thunar} </usr/share/pixmaps/thunar>

Thunar then shows at the very top of the right-click menu.

-merlin

---

### Post by Ripfox on 2007-08-30
But I am using FVWM-Crystal...:)

---

### Post by merlinus on 2007-08-30
Sorry.  I thought you switched from fluxbox because of not being able to create a menu item for thunar.

-merlin

---

### Post by Ripfox on 2007-08-30
Anyone else have any ideas?

---

### Post by urukrama on 2007-08-30
It isn't that different for fvwm-crystal. I no longer have it installed, but if I remember correctly, you'll need to add an entry in the file that governs your theme preferences. If you have other menu entries, look for the syntax of those, and just fill in the right spots for thunar. It isn't that hard, I've done it before, but can't remember how. If you want, post your theme/style configuration file, and someone might be able to tell you what to do.

Fvwm-crystal's configuration files are a bit more complex than, say, Openbox', but they are comprehensible. If you're having a hard time, you can also look for help on the [FVWM forums]("http://fvwm.lair.be/").

---

### Post by Ripfox on 2007-08-30
When i look in .fvwm, all there is:

file:///home/imac/.fvwm/preferences/LastChoosenWindowDecoration

file:///home/imac/.fvwm/preferences/LastChoosenWallpaper

file:///home/imac/.fvwm/preferences/LastChoosenRecipe

file:///home/imac/.fvwm/preferences/LastChoosenColorset

file:///home/imac/.fvwm/preferences/LastChoosenButtonModel

file:///home/imac/.fvwm/preferences/DefaultTerminal

file:///home/imac/.fvwm/preferences/DefaultDesktopManager


But in the DefaultDesktopManager file, all it says is:

LoadPreferences LastChoosenWallpaper

Weird? Those entries seem to have nothing to do with the "desk manager" (is that the "file manager"?)

---

### Post by urukrama on 2007-08-30
You need the 'recipe' file. Locate it, and then add/edit the appropriate line.

---

### Post by Ripfox on 2007-08-31
Where is that?

---

