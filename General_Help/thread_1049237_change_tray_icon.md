---
title: "change tray icon"
date: 2009-01-24
forum: General Help
---

### Post by syco on 2009-01-24
hi.
is the first time I write on the international forum, sorry for my English by "google translate" 
I wanted to know if you can change the icons that appear in the systray and taskbar gnome, but with the theme icons firefox, thunderbird and other programs when minimized those are always the default.
You can do something?
thanks.

---

### Post by MikeBrown on 2009-01-24
If I read your post correctly, all you will need to do is right click the icon, and click "properties". Once the properties screen opens, it will show your icon on the left hand side. You can click the icon and it will open your file browser. Navigate to the icon you want to use and click open. 

That should be all that you need to do!

---

### Post by syco on 2009-01-24
no, I think that's wrong, even if this is the fault of my previous post.
however, I wanted to say that when I change the theme of icons, in Applications -> Internet, firefox icon changes depending on the chosen theme. But when I start the program in the taskbar and traybar always use the default icon.
this time I attached a screenshot, I hope go well ...

---

### Post by mc4man on 2009-01-24
You can probably change the icon by going in a terminal
alacarte

Then you'd highlight your internet in left box and right click on the app (firefox) in the right side box -> properties and change the icon there.

Maybe copy and save the orig. icon location before changing in case you want to restore

---

### Post by syco on 2009-01-24
I have already changed the icon from alcarte and the menu is the icon that I chose. is the icon of tskbar that is always the default.

---

### Post by blackened on 2009-01-24
You might try changing the firefox and thunderbird icons (symlinks) in /usr/share/pixmaps.

---

### Post by mc4man on 2009-01-24
You can do it if you want. The icons used are in /usr/lib/firefox-3.05/chrome/icons/default
The default16.png is the one your probably after. (you'd need to use same size .png
You can use a larger than 16x16 if it's the first valid size found and it will be  scaled to fit, for instance if your icon is 48x48 just remove all the icons and insert yours, default32.png or default48.png

For the upper panel if desired that's in a firefox.desktop (you need to insert path, I don't believe size matters except for clarity

```
gksudo gedit /usr/share/applications/firefox.desktop
```
scroll down to icon= line

Again I'd back up the originals in /usr/lib/firefox-3.05/chrome/icons/default

---

