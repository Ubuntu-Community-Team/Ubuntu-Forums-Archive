---
title: "Just two small issues"
date: 2005-04-18
forum: Desktop Environments
---

### Post by akinwale on 2005-04-18
I uninstalled Firefox 0.99 using Synaptic and installed version 1.0.2 using the binary package from mozilla.org
I've been trying to get the default "globe" icon (the same icon as the Internet menu under Applications) - I like it - but I cannot find it. I've looked over and over again in /usr/share/pixmaps with no success. Perhaps, I may have missed it. Does anyone know the exact location of the icon file?

I'm also trying to customise my menus. When I try to add a launcher, it doesn't work. After I click on OK, nothing happens. I access it by opening the location "applications:///" in the file manager. Perhaps, I'm missing something? Or maybe I need root permissions? How can I solve this?

Thanks.

---

### Post by nad on 2005-04-18
/usr/share/pixmaps/mozilla-firefox.png | xpm.

As far as editing your menus. Doing this through gnome is broken. See several threads here regarding menu editing.

The launchers are found as .desktop files in /usr/share/applications (they are 'hidden' files). These can be edited and new ones added manually. You will have to be root to make persistent changes.

Dan M

---

### Post by akinwale on 2005-04-18
Hmm... after rebooting, I found out that the launcher items were added to the menu. Also, I didn't find the icon specified, but I found a similar icon that is quite similar located in /usr/share/icons/Human/scalable/apps/firefox.svg
The colour seems too bright though, still hoping to get the previous one.

---

### Post by byourg on 2005-04-18
look in /usr/lib/mozilla-firefox/icons or the folder where you installed firefox there will be a icons folder.

---

