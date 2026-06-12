---
title: "Can I add a custom menu to the panel??"
date: 2009-08-08
forum: Desktop Environments
---

### Post by davbren on 2009-08-08
Hey all. I was looking at the eyeOS screenshots and it has menus much like Gnome at the top of the screen on the panel. I was wondering if I can make custom menus on the Kpanel? would I have to make a plasmoid?

---

### Post by Zorael on 2009-08-08
One way would be to create directories someplace with launchers (.desktop files) - one for each menu you want to create, with the launchers you want that menu to contain. Then add folder view widgets (not quickaccess browsers) to your panel and point each to each directory. A roundabout way, but I don't think there's an easy plasma menu widget that doesn't just contain the normal menu entries (application launcher).

---

### Post by davbren on 2009-08-08
Ah yh, i thought it'd be something like that thanks. 

Also, I'm using the web browser plasmoid, is there a way to install flash for it?

---

### Post by Zorael on 2009-08-08
Well, even JavaScript support is missing, I think. Alternatively disabled by design; someone in #kde @ irc.freenode.net should know.

---

### Post by davbren on 2009-08-11
Also, how do I change the colour of the Kpanel. I know there are plenty of themes out there but generally I'm happy with the theme i just would like to change the colour slightly.

---

### Post by Zorael on 2009-08-11
It's just "the panel" now that it's taken care of by plasma.

You'd have to modify the actual panel background image and tint it the way you want. Themes are in **/usr/share/kde4/apps/desktoptheme/**. Edit one and save the changed one to **~/.kde/share/apps/desktoptheme/**. Do note that there is one picture for an opaque panel (compositing off) and one normal one (compositing on).

---

