---
title: "Gnome Shell Panel Font tip..."
date: 2012-02-16
forum: Desktop Environments
---

### Post by slickvguy on 2012-02-16
Been playing with a lot of other distros lately, but I just spent a few hours with Ubuntu 11.10 and gnome shell, and I realized something that might be of use to others. 

My panel text (font) was looking horrible for some reason, even though fonts were fine in all other places. I had enabled hinting and anti-aliasing, as usual. Installed a few fonts (Segoe UI is still my favourite). All looked fine...except for the top panel and it's menus.

After a bit of snooping, I saw that the font was supposed to be Cantarell per gnome-shell.css. WHen I did a fc-match 'cantarell' it was linked to Deja Vu Sans! WTF??? I checked the installed fonts, and lo and behold, gnome-shell package did NOT install the cantarell font! So I installed the Cantarell package and the panel text now looks much better. While the fonts are not as sharp as they are throughout the rest of the system (something to do with Clutter/Mutter and subpixel?), it's still a huge improvement over Deja Vu Sans. lol. 

Also, I reduced the applications grid icon size, etc., so that many more icons are displayed. Far less annoying than the default size. Search for the how-to.

With extensions and a few other mods, gnome shell si becoming ALMOST bearable, but I'm still nto sure if I'll stick with it and/or Ubuntu.

---

### Post by Nosferax on 2012-09-07
Thanks, I installed it and it fixed some ugliness for me too!

---

