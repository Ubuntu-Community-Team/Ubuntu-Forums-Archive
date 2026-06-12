---
title: "Icon for firefox in applications menu?"
date: 2005-04-17
forum: Desktop Environments
---

### Post by Stephen-I-M on 2005-04-17
Should my hoary install have an icon for firefox in the Applications->Internet menu? If so, how can I restore it? Thanks.

Stephen

---

### Post by TravisNewman on 2005-04-17
It could be related to the theme you're using

If you're using a theme without a firefox icon that doesn't inherit another theme, that could leave it blank.

---

### Post by mokum on 2005-04-17
You can always add the icon by hand bij adding: 'Icon=mozilla-firefox.png' (without the quotes) in /usr/share/applications/mozilla-firefox.desktop.

If there is such a line in the mozilla-firefox.desktop, the icon it points to is probably not present (the icon should be in /usr/share/pixmaps).

Apps can also add '.desktop' files in /usr/share/gnome/apps subdirectories, e.g. /usr/share/gnome/apps/Internet/dillo.desktop. 
If the file doesn't contain a 'Categories=...' line, the app shows up as the content of a folder in the menu, rather than as a menu subitem.

Et

p.s. I don't really know if it's a good idea to add, remove or change these entries by hand..

---

### Post by ggeneraux on 2005-04-20
[QUOTE=Stephen-I-M]Should my hoary install have an icon for firefox in the Applications->Internet menu? If so, how can I restore it? Thanks.

Stephen[/QUOTE]
 I've noticed that after installing a new program (this is with Gnome as desktop environ) the menus don't update with the correct icon until after I log out and then log back in.  Also, specifically with Firefox, there is an icon in /usr/share/pixmaps called 'mozilla-firefox.png' which is only a non-descript globe, and not the normal Firefox icon that you would expect.

---

### Post by shakin on 2005-04-20
SVG icons are the best quality and they scale well to different sizes. Various Gnome themes come with them. To find a firefox SVG icon run 'locate firefox |grep svg |grep scalable' from the command line. You'll see something similar to this:

/usr/share/icons/Human/scalable/apps/firefox.svg
/usr/share/icons/Human/scalable/apps/mozilla-firefox.svg
/usr/share/icons/Nuvola/scalable/apps/firefox.svg

Browse those locations with Nautilius to find the one you like best. In this case you want /usr/share/icons/Nuvola/scalable/apps/firefox.svg because the others are the globe icon.


P.S. SVG icons look incredible with the gdesklet starterbar.

---

### Post by shakin on 2005-04-20
I just realized that Ubuntu doesn't come with the Nuvola theme.  You can grab it at [http://librsvg.sourceforge.net/theme.php](http://librsvg.sourceforge.net/theme.php).

I have all those themes and they provide a very nice set of SVG icons. I switched all of my icons to ones from these themes.

---

### Post by Bob D. on 2005-04-20
You can get the regular Firefox icon here also: [LINK]("http://fedoranews.org/tchung/firefox/0.9.3/firefox.png")

Bob

---

### Post by Psquared on 2005-04-29
I had this problem after installing Acroread. There was a menu entry but no icon. The AdobeReader_GNOME.desktop file had an "icon=acroread.png" line, but apparently it could not find the icon so I edited it to point to the exact location of the .png file. It showed up after that.

---

