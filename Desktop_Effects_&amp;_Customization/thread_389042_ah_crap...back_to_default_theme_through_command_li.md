---
title: "ah crap...back to default theme through command line?"
date: 2007-03-20
forum: Desktop Effects &amp; Customization
---

### Post by JCasper on 2007-03-20
I dropped a mouse theme into the windows appearance theme and my panels and my icons on desktop vanished. I can open browser and command line as of now...oops...anyone know how to reset theme back to default through command line???
I guess that is what I need...

NOOOB...LOL

---

### Post by bapoumba on 2007-03-20
If you remember the theme name, from CLI you got to ~/.themes and delete it. **ls** will list the .themes content.
```
cd ~/themes
ls
rm -R <file_name>
```
Logout and log back in your session. The default theme should be used.

---

### Post by JCasper on 2007-03-22
ok, tyvm. What I did though and just forgot to edit quickly enough was ctrl alt backspace. came in with a regular gnome session and deleted the bad theme. Had to reset a few icons, but no biggie.

---

### Post by 16777216 on 2007-03-30
I did the same thing by accident but, there is no directory or file or anything for that matter in the ~/.theme directory related to the cursor theme that I "installed" accidentally.

I have tried to run **gnome-theme-manager** and **gconf-editor** from the command line both give this warning:  
```
(gconf-editor:26269): Gtk-WARNING **: Theme file for Vanilla-DMZ-AA has no directories


(bug-buddy:26276): Gtk-WARNING **: Theme file for Vanilla-DMZ-AA has no directories
```
I would like to reset the theme to default as gnome does not even start now.

---

