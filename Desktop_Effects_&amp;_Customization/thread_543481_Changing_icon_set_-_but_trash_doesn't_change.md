---
title: "Changing icon set - but trash doesn't change"
date: 2007-09-05
forum: Desktop Effects &amp; Customization
---

### Post by freesitebuilder on 2007-09-05
I changed from Human to try some other icon sets, but I now find that everything changes except trash. 

This describes a similar problem [http://ubuntuforums.org/showthread.php?t=278273](http://ubuntuforums.org/showthread.php?t=278273) (now closed), and the advice is
> I've resolved adding "user-trash-empty.svg" & "user-trash-full.svg" to all directories of icon theme...

I have the .png files in the icon directory OK, so should I create an .svg version and place it in the directory? :confused:

TIA

---

### Post by ayoli on 2007-09-05
no, you  just have to add "user-trash-empty.png" & "user-trash-full.png" in the subdirectory called "places" in your iconset folder.
you can do that with making links to the trash (empty & full) of your icon set.

---

### Post by petit.padavoine on 2007-09-05
> **ayoli said:**
> no, you  just have to add "user-trash-empty.png" & "user-trash-full.png" in the subdirectory called "places" in your iconset folder.
you can do that with making links to the trash (empty & full) of your icon set.

Your icon set probably uses the files "gnome-stock-trash" for the trash icons, whereas Ubuntu uses "user-trash". Just rename the gnome-stock-trash files to user-trash, ie, instead of "gnome-stock-trash-full.png", "user-trash-full.png"

---

