---
title: "a little bit messy"
date: 2009-03-07
forum: Desktop Environments
---

### Post by houcem on 2009-03-07
Does the installed applications under different desktop environments melted together in the Gnome and the KDE menus?Do they interact? I remember when I was using Open Suse It was the case!

---

### Post by jpeddicord on 2009-03-07
They do: Qt apps will still show on GNOME and GTK apps will show on KDE. You can disable this by manually editing your menus in each desktop environment, or by manually editing your .desktop files in /usr/share/applications and settings OnlyShowIn on each desktop-related application. It's a pain to do all of that though.

---

