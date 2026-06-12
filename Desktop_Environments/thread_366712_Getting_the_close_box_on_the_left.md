---
title: "Getting the close box on the left"
date: 2007-02-21
forum: Desktop Environments
---

### Post by jiminy on 2007-02-21
I'm a recovering Macintosh user who's just installed Ubuntu Edgy, and having the close/minimise/maximise buttons on the right of the title bar reminds me entirely too much of that *other* operating system. :) I'm trying to figure out how to relocate the close box to the left side, Mac-style, without changing too much else. The easiest way seemed to be simply downloading a new Metacity theme. Unfortunately, searching [http://art.gnome.org/]("http://art.gnome.org/") and the like I've only found themes which give the windows the same colour scheme as Mac OS X or OS 9 without actually changing the location of the buttons, which is the opposite of what I want. Can anybody help?

---

### Post by engineer on 2007-02-21
there's a gconf key, which changes the order of the buttons.

you can find it with gconf-editor in apps/metacity/general.
the key is called button_layout

---

### Post by jiminy on 2007-02-22
Well, that was a lot quicker than I thought it would be. (For any newbies reading this: gconf is the Configuration Manager, which can be found in the System>Preferences menu---you may need to activate it in Menu Layout first. Find the key as described above, rearrange the buttons the way you want, and it'll happen instantly. No need to reboot or even relaunch running programs.) Thanks!

---

### Post by 2cute4u on 2007-09-18
What about if you are using beryl, compiz or compiz fusion?

---

