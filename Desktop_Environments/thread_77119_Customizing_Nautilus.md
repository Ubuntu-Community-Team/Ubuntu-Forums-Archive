---
title: "Customizing Nautilus"
date: 2005-10-16
forum: Desktop Environments
---

### Post by oliver123 on 2005-10-16
Hello,
I've got some questions about concerning Nautilus in Breezy:

1) Is there a way to make the address bar show the written address (not the buttons) in every new window? Currently I can switch that with Ctrl + L, but I'd like to make it permanent.

2) Is it possible to merge the address bar and the icon toolbar together into one single bar? Currently the address bar is below the icon toolbar, and that takes a lot of space.

3) Can I make the icons in the icon toolbar smaller? Again, they take lots of precious space now :)

4) Finally, can you recommend a good-looking icon theme? On my KDE desktop I have crystal-svg and like that; is there a similar theme for Gnome with good-looking icons for 16 and 32 pixels? The currently-installed themes have quite bad icons for symbolic links and write-protected files; and also I think most of the themes look somewhat ugly overall ;)

Thanks for your help,
Oliver

---

### Post by manicka on 2005-10-16
1)
alt-f2
gconf-editor

apps-->nautilus-->preferences

check

always_use_location_entry

---

### Post by manicka on 2005-10-16
There is a crystal iconset for gnome. search for it at gnome-look.org

---

### Post by yage on 2005-10-16
1. Yes this is possible... Open your gconf tool and go to > apps > nautilus > preferences and check the box saying "allways_use_location_entry"

2. Don't think this is possible but you can remove the icon toolbar:
start up nautilus as browser goto view > and uncheck main toolbar (dunno if this is the right name since i'm using norwegian layout)

3. To make the icons smaller use another theme for Gnome

4. This i don't know anything about since i haven't used KDE for years...

I hope this helps you on your way :smile:

---

### Post by bvc on 2005-10-16
2) not possible but I wish it was

3) make a file called .gtkrc-2.0 and put it in your home directory. Put this in it and edit to your liking.```
gtk-icon-sizes = "panel-menu=24,24:panel=16,16:gtk-menu=16,16:gtk-large-toolbar=20,20"
```
then either reset the theme or killall nautilus

4) [http://www.crystalgnome.org/index2.htm](http://www.crystalgnome.org/index2.htm)
[http://gnome-look.org/content/show.php?content=26331](http://gnome-look.org/content/show.php?content=26331)
[http://gnome-look.org/content/show.php?content=24758](http://gnome-look.org/content/show.php?content=24758)
[http://gnome-look.org/content/show.php?content=24840](http://gnome-look.org/content/show.php?content=24840)

---

