---
title: "Firefox icons messed up"
date: 2010-01-07
forum: Desktop Environments
---

### Post by ratcheer on 2010-01-07
My Firefox icons went haywire. On the Panel at the top of the screen, it now looks like a blue ball with a vague highlight image on the face. On the main Application Menu, it looks like a flat square of something on top of a spring (???).

So, I learned how to change the icons by going to the properties of each object. But, I still could not find the real Firefox icons to change to.

Next, I found the official icons on the Mozillazine site and downloaded a 16x16 and a 32 x 32 .png file of them. But, when I go from the object properties dialogs of the Panel and Main Menu entries and navigate to the directory where I saved them, they do not show up at all. When I look in the directory, itself, they are there.

I am lost. Why can't I fix my icons?

Tim

---

### Post by chraazy on 2010-01-19
I have problem with my firefox icons as well. I have changed every firefox icon in my system. even the one named mozicon. yet, whenever i open firefox, the icon in the window list, window picker, window applet or any other panel applet, is still that ugly little icon that is default. it won't change. its about to drive me insane. i really am lost.

---

### Post by ratcheer on 2010-01-19
When I installed an update a few days ago, the one on the screentop panel changed back to a Firefox icon, but the one in the applications menu is still the funny little board with a spring on the bottom.

I did find some posts out on the internet about changing the Firefox icons, but the procedures were very involved.

Tim

---

### Post by mister_playboy on 2010-01-19
Some themes (such as Ubuntu Studio) modify the appearance of the icon, and it may not revert to the original when changing back away from that theme.

To fix the icon in the Applications list: Right click on Applications and pick Edit Menus.

In the screen that opens, click on Internet in the left pane, then Firefox in the right pane, and then properties on the far right.

In the small box that open, click on the springboard icon on the left side, and type /usr/share/pixmaps in the box at the top of the "Browse icons" box.  You should find it as mozicon128.png or firefox-3.5.png.

Fixing panel launchers is easier... right-click and pick properties, and you do the same as above.  The location to find theme-specfic icons is in /usr/share/icons.

---

### Post by ratcheer on 2010-01-19
Awesome! Thank you very much, mister_playboy!

Tim

---

### Post by sigurnjak on 2010-01-19
Icons you are looking to replace are in usr/lib/your current firefox version folder/chrome / default  and user/lib/your current firefox/icons .
REPLACE THEM AFTER  EACH UPDATE  to keep ones you like .

---

