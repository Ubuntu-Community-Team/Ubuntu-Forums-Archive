---
title: "Find out location of icons"
date: 2006-02-16
forum: Desktop Environments
---

### Post by TheIdiotThatIsMe on 2006-02-16
Hi, is there a way to find out the location of the pictures used for desktop icons. I know some are stored in /usr/share/pixmaps, but some are not and I am having trouble locating them (including one for amaroK-SVN, OpenOffice.org 2, etc.)

---

### Post by Qrk on 2006-02-16
It depends of the theme you are using. If the icon comes from a theme you isntalled through the theme manager, it will be in ~/.icons/themename ( most of the time its one of the subfolders, such as "/scalable/apps")

The default Gnome icons (if there isn't a custom icon you selected, and your theme doesn't supply one) are in /usr/share/icons/gnome. You can also install your icon themes to /usr/share/icons/ so they show up in root programs.

Edit: I believe they are in .../gnome, but I haven't used the default set in a long time, so I could be wrong.

---

### Post by TheIdiotThatIsMe on 2006-02-16
Unfortunately I am still unable to find any icons for certain apps such as amaroK and OpenOffice.org

---

### Post by Qrk on 2006-02-17
On my computer at least:

OO.o2

/usr/share/icons/gnome/48x48/apps

I don't have amarok installed.

---

### Post by art on 2006-02-17
you can also try to find them, e.g. 
locate amarok.png 
or locate amarok.xpm, etc... I was always able to find the icons I needed with these. For instance here is where my amarok.png is 
/usr/share/icons/hicolor/48x48/apps/amarok.png.

---

