---
title: "Frostwire icon won't change in the awn menu"
date: 2008-01-10
forum: Desktop Effects &amp; Customization
---

### Post by Rubruquis on 2008-01-10
I am able to change every icon in the AWN menu, but surprisingly, I cannot change the Frostwire icon.
I know I can replace the icon in /usr/share/icons, but I just want to change the icon in the AWN menu (like I did with the other applications).
Another interesting thing, that may be related, is that when I open AWN Manager and look at the Launchers, I don't see any icon next to Frostwire, it is blank. So I am thinking that it may be using the icon directly from /share/icons folder and that's why I am not able to change it.
Do you know if there is a way to change the icon only in AWN menu?

---

### Post by rune0077 on 2008-01-10
Try removing it from AWN, then add it through launchers instead of just dragging it to the AWN-bar. When you add the launcher you should be able to select your own icon for the application.

---

### Post by Rubruquis on 2008-01-11
> **rune0077 said:**
> Try removing it from AWN, then add it through launchers instead of just dragging it to the AWN-bar. When you add the launcher you should be able to select your own icon for the application.

It doesn't work either. When I add to the launcher, it appears in Launcher but it doesn't appear in the AWN menu.

---

### Post by rune0077 on 2008-01-11
After adding it, have you tried restarting AWN? It's sometimes not enough to click the refresh button, you need to close AWN and start it again.

---

### Post by Rubruquis on 2008-01-11
I've restared AWN and frostwire shortcut was there, but still the icon does not change.

---

### Post by rune0077 on 2008-01-11
You need to set the icon you want *when adding the launcher*, not from the actual dock. Otherwise, try going to home/.config/awn/launchers. Locate the app there, right click on it, select properties, click the icon from the window that pops up and set a new icon. See if this works.

---

### Post by Rubruquis on 2008-01-11
I was not able to add PNG format while adding to the launcher, it only accepted SVG.
But the second method worked for me =) Thank you really very much for reading all my posts and answering each of them, suggesting something new.

---

