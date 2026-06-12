---
title: "Trouble installing a gtk2 theme"
date: 2008-02-09
forum: Desktop Effects &amp; Customization
---

### Post by Aiello on 2008-02-09
I downloaded a gtk2 theme from [www.gnome-look.org](www.gnome-look.org) called LiNista2 and I am having some problems installing it. It seems to be more than just a gtk2 theme, because when I use the appearance manager, or what ever it is called, and I select to install it, it tells me that the file format is invalid. So, I opened up the file and I found specific instructions to install it. They say "GTK2 and Metacity(Controls and Window Decorators): copy the patch LiNsta2 to /usr/share/themes". I am guessing that "patch" means "path". I then open two nautallis windows and try to drag and drop the file into /usr/shar/themes, but the file doesn't get moved there. I am a true beginner at Ubuntu and Linux, so I know my explanation might not make a lot of sense, but any help would be appreciated!
-Thanks!

---

### Post by Tenken on 2008-02-09
/usr/share/themes is a system directory so you need administrator permissions to access it. You can open the nautilus window with the right permissions by hitting alt+F2 and type 

```
gksu nautilus
```

or in a terminal type

```
sudo cp /path/to/gtk/theme /usr/share/themes
```

---

### Post by Aiello on 2008-02-09
When I open this new file browser and go into Desktop (where the theme is saved) there is nothing there. Should I save the theme in a different location?
-edit- nvm that. I found how to get into it.

---

### Post by Aiello on 2008-02-09
Ha, that worked! Thanks for the help!

---

