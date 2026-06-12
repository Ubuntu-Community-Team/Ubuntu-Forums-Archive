---
title: "Undo GTK theme switcher changes?"
date: 2007-04-16
forum: Desktop Effects &amp; Customization
---

### Post by darundal on 2007-04-16
I installed GTK theme switcher a while back (I don't even know why, really) and switched the GTK theme. Now, whenever I try to change it with the built-in theme switching utility under system, it refuses to change. Not everything, only the my gnome panels refuse to change. I tried uninstalling GTK theme switcher, which had no effect whatsoever. Anyone know what file it writes to, and how what changes need to be made so that I can use the built in theme switcher to change the GTK theme so that the gnome panels change when everything else does as well? Thanks.

---

### Post by jordanmthomas on 2007-04-16
```
rm ~/.gtkrc*
```
The theme switcher puts its choices in these files and gnome looks there before wherever gnome-theme-manager stores its settings.  Solution:  remove the config files made by the theme switcher.

---

