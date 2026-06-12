---
title: "Keyboard sortcuts and xgl/compiz"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-07-10
I previously had a shortcut set up so that ctrl+shift+t opened a new terminal window.  I set this up via system>preferences>keyboard shortcuts.

Since installing xgl/compiz this no longer works - I think because I am using the X keyboard settings.  How do I create a new shortcut to do this.  I tried in the gset-compiz configuration tool, but it doesn't work.

---

### Post by frodon on 2006-07-10
It's because system>preferences>keyboard window is related to metacity window manager therefore those shortcuts works only if you run metacity.
In this case xbindkeys is a good alternative :
[http://doc.gwos.org/index.php/GnomeKeyboardShortcut](http://doc.gwos.org/index.php/GnomeKeyboardShortcut)

---

### Post by CamB on 2006-07-11
Or, as I've just found out, you can set it in gconf-editor. 

In gconf-editor, go to >apps>compiz>general>screen0>options

Edit command0 and make it gnome-terminal (or whatever you want)
Edit run_command0 and make it <Control><Shift>t (or whatever you want)

---

### Post by Lunar_Lamp on 2006-07-11
If that works for you CamB, then great, but I couldn't get it to work.  Quite possible that I made an error, though I did try several times.  I managed to get xbindkeys to work without too much hassle (though I think the UI could do with some work).

---

