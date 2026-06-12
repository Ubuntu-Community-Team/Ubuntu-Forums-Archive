---
title: "creating, installing custom laucher icons"
date: 2009-02-26
forum: General Help
---

### Post by mickeyf on 2009-02-26
I have created svg icons (also 48x48 png icons), but they are not visible via the launcher properties dialog, and I don't know how to install them. I have changed the permissions to match those in /usr/share/icons/gnome/scalable, which is where the only ones visible seem to be. 

What's the trick to getting a home-made icon (of whatever format) recognized and usable?

tia

---

### Post by andonato on 2009-02-26
Put them in the folder where all your other icons are, then right click on the launcher, select properties, click the "Basic" tab, click on the current icon (next to the "name" field). This will bring up a window where you can then navigate to the new icon.

---

### Post by mickeyf on 2009-02-26
> **andonato said:**
> Put them in the folder where all your other icons are, then right click on the launcher, select properties, click the "Basic" tab, click on the current icon (next to the "name" field). This will bring up a window where you can then navigate to the new icon.
This is exactly what I did - except there is no "Basic tab." I am running Ubuntu 8.10. My home made icons are in the same folder with the same permissions as the stock icons, but only the stock icons show up when accessed this way.

---

### Post by andonato on 2009-02-26
Try putting them in /usr/share/pixmaps and see if that helps.

---

### Post by mickeyf on 2009-02-26
> **andonato said:**
> Try putting them in /usr/share/pixmaps and see if that helps.
I did. It didn't.

---

### Post by mickeyf on 2009-02-27
The problem seems to be in the file browser for the panel. 

I have two application launchers. One, by default uses a pixmap (.png) icon. The other, by default, uses a .svg icon. When I attempt to replace the icon for either of them, the 'browse' button takes me directly to the folder for the default icon, either

/urs/share/icons/gnome/scalable/apps (for the .svg), or

/urs/share/pixmaps (for the .png). Even if I place my new icons in those folders, they are not visible - only the original icons are.

If I use the browse button to navigate to any other folder, no icons are visible in that folder, even though they are visible when using the file manager.

However, if I directly edit the path in the edit box adjacent to the browse button, I can navigate to any folder and all the icons there are visible and available. 

It appears that navigating via the browse button only shows a specific (originally installed) set of icons in specific locations, and doesn't let you 'browse' at all.

I would call this a bug, and a work-around.

---

