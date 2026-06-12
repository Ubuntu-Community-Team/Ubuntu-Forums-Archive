---
title: "Taskbar icons in Gnome don't match the icon theme"
date: 2007-12-08
forum: Desktop Environments
---

### Post by toxin on 2007-12-08
How comes that taskbar icons in Gnome don't match the icon theme? I don't mean the launchers, but the tasks in the window list (see attached snapshot). 
The workspace selector too is affected by this behaviour. Is there any workaround?

Thanks.

---

### Post by kryth on 2007-12-08
Yeah, me too. I wish I knew how or if you can.

---

### Post by toxin on 2007-12-09
Actually it seems that only some programs are affected by this problem (e.g. firefox, thunderbird, gterm, gimp, avidemux, etc.). 
While those programs are loading the icon is the one from the theme, but then it switches to default.
So maybe the point is not gnome, but the way those programs handle their icon?

Does anybody have any clue about this, please? 
Are kryth and me the only ones who experience this behaviour?

---

### Post by ingvildr on 2007-12-09
Well firefox gets the taskbar icon from here
```
/usr/share/firefox/icons
```
Usually if its not matching your theme either look for icons in /usr/share/pixmaps or in /usr/share/NAMEOFPROGRAM that tends to be the main places for default icons.

---

### Post by toxin on 2007-12-10
Yep, every application stores its default icon in /usr/share/pixmaps. But what I'm trying to figure out is why some apps have their icon replaced by the theme, while others don't :confused:

---

### Post by ingvildr on 2007-12-10
On the front of firefox, it has a visual identity that is recognizable to many users it wants to keep that, other apps may have similar views.

As i said before firefox gets its taskbar icons from
```
/usr/share/firefox/icons
```
That is the only place it will look, it is to the best of my knowledge hard coded to that, it will not look for GNOME or KDE icon sets, other applications do this too, mostly popular cross platform ones.

---

### Post by toxin on 2007-12-10
Oh I see, it's a deliberate choice. But then theme designers should avoid those shiny and fancy icons they put for those apps. They're very nice but IMHO having inconsistent icons on menus/launchers and taskbar/awn/etc. is quite annoying.

BTW I'm positive that, in the case of apps as gterm or synaptic, it could just be an oversight.

---

