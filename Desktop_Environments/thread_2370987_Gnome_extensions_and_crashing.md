---
title: "Gnome extensions and crashing"
date: 2017-09-09
forum: Desktop Environments
---

### Post by Robbyx on 2017-09-09
In Gnome Tweak there is a tab to switch on/ off  the gnome extensions that are installed. If there is a system crash it is usual to find all the extensions have been turned off.

Is there a directory or file that I can backup and restore so that the extensions are switched on automatically after a crash?

Robin

---

### Post by Frogs Hair on 2017-09-09
What release ? Many extensions on the development release are broken. You toggle extensions on and off from the gnome extensions website.

I don't think the schema's will help you auto start the extensions they simply store the settings for the extension. The extensions on my system installed from the repository have the schema's in usr/share/glib-2.0 and for extension from the site they are in home .local/share/gnome-shell.

---

