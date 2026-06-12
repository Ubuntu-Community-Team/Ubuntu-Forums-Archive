---
title: "Change Theme From Terminal"
date: 2009-01-20
forum: General Help
---

### Post by quigibo on 2009-01-20
This is my first time posting :)  I've always used google in the past to search for and solve 100s of my linux related questions but this is the first time I couldn't find anything and its driving me crazy!  This is a question about the gnome appearance manager.

Just for fun, I wrote a script to randomly change the theme color on each boot to spice things up a bit.  But even though it modifies the theme file correctly, it doesn't actually update the theme until I manually go into the appearance settings and change the theme from 'custom' back to my theme (because it keeps changing to custom for some reason)

Is there any kind of terminal command to change and then update the theme that I could put into a bash script?  Or is there another method to this madness?

---

### Post by Tibuda on 2009-01-20
I can't understand what you want, but you can change many Gnome settings with gconftool-2. This script will change the metacity, GTK, icon and font:
```
# Change the metacity theme (window borders)
gconftool-2 --type=string -s /apps/metacity/general/theme **themename**

# Change the GTK theme (controls)
gconftool-2 --type=string -s /desktop/gnome/interface/gtk_theme **themename**

# Change the icon theme
gconftool-2 --type=string -s /desktop/gnome/interface/icon_theme **themename**

# Change the font
gconftool-2 --type=string -s /desktop/gnome/interface/font_name "**fontname 12**"
```

Ed

---

### Post by quigibo on 2009-01-20
Oh thank you!  I'm getting closer now.  I can change the themes, however, its only allowing me to change to the default themes (ex: Human).  I need to change it to one of my saved themes that are in my ~/.themes folder.

If I put the name of my saved theme into the gconf key, it says that no themes exists with that name.  I'm guessing that's because my saved themes aren't actually *themes*, but theme configurations?  I'm not sure.  All help is appreciated, thank you!

---

### Post by Tibuda on 2009-01-21
I think you are right, the "saved themes" are only references to Metacity/GTK/Icon/Cursor themes. Sorry, I don't know how to help.

---

