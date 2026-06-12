---
title: "Want to change main menu items icon sizes."
date: 2008-12-26
forum: General Help
---

### Post by cdahmedeh on 2008-12-26
Hello,

I just would like to know how to change the size of the icons of the items in the main menu. I think they are too big.

Thanks

---

### Post by Ivo Moelans on 2008-12-26
Icon sizes are usually determined by the theme you are using. 

1) If you want to change them for the current theme alone, open */home/<username>/.themes/NameOfTheme/gtk-2.0/gtkrc* with Text Editor. Look for al line like this:

```
gtk-icon-sizes = "panel=16,16 : panel-menu=16,16 : gtk-menu=16,16 : gtk-button=20,20 : gtk-small-toolbar=16,16 : gtk-large-toolbar=24,24 : gtk-dialog=32,32 : gtk-dnd=32,32"
```

Usually at the very beginning of the file or at the end. If the line isn't there you can simply add it. Save the file, log out and log in.
This code gives you very small icons in the menus, but you can play around with the sizes until you're satisfied with the results.

2) If the theme you're using is installed globally, the gtkrc file is in */usr/share/themes/NameOfTheme/gtk-2.0/*

3) If you want to change the icon size for **every** theme you use, look for a file called *.gtkrc-2.0* (this is a hidden file: press *Ctrl+H* to make visible) in your home directory. Open it and place the code in that file. If the file doesn't exist, *make* it with Text Editor (New file, copy and paste code, Save as */home/<username>/.gtkrc-2.0*) (don't forget the leading "."). This file supersedes the gtkrc file of the themes.

Hope this helps.

---

### Post by cdahmedeh on 2008-12-29
OK, I did the steps in number 3 and it worked perfectly. You even got the size just right !

---

### Post by Ivo Moelans on 2008-12-30
You're welcome.

---

### Post by ubseamus on 2011-01-02
I have been trying to do the same. That is, make the icons in my top panel smaller, the ubuntu logo next the the Applications menu, quick launch icons, etc.

After reading this thread I created the file:

/home/seamus/.themes/SMS/gtk-2.0-key/gtkrc


It contains:

# Added by Seamus on 02-01-2011
#

gtk-icon-sizes = "panel=16,16 : panel-menu=16,16 : gtk-menu=16,16 :  gtk-button=20,20 : gtk-small-toolbar=16,16 : gtk-large-toolbar=24,24 :  gtk-dialog=32,32 : gtk-dnd=32,32"


I have selected a custom theme "SMS" via "System->Preferences->Appearance" menu option, rebooted, and there is no change. 
The original icons are much to large on my laptop, so I have selected a different in my custom theme, which are smaller buy default, but they do not look so nice.

Please help...  :?:

---

### Post by Rodu on 2011-01-08
So did I follow the steps suggested by Ivo on pass three. It worked well.
It would be nice if they would review the size by default in the next releases since I think they are a bit big while using smaller icons the menus etc look more cool.


One thing that I don't like is the fact that I would like the position of the window icons for close, minimise, and maximize to stay on the LEFT as I choose via the gconf-editor. While when playing with appearance themes it keeps every time to move them again on the right!!

Anybody knows if this setting could be set once and kept somehow for any theme?

Thanks all.

---

