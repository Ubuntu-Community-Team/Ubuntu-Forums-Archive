---
title: "Changing the login screen after screensave mode"
date: 2009-02-14
forum: General Help
---

### Post by davidself1001 on 2009-02-14
Is there a way to change the panel that asks for your password after your screensaver kicks in?

---

### Post by davidself1001 on 2009-02-15
Anybody got a clue on this?  I did something with this at one time because there is an icon on that panel that I put there but I can't remember where I did it.  I am over 50 so my memory ain't what it used to be.

---

### Post by mcduck on 2009-02-15
Gnome-screensaver is the program responsible of the login window when returning from locked screen (or screensaver).

You can find themes for the dialog here: [http://gnome-look.org/index.php?xcontentmode=187]("http://gnome-look.org/index.php?xcontentmode=187")

Just extract the theme to /usr/share/gnome-screensaver/, then run gconf-editor, browse to apps/gnome-screensaver and change "lock_dialog_theme" from "default" to whatever your new theme is called.

---

### Post by davidself1001 on 2009-02-15
thank you so much.  that did the trick.  while i have your attention, how do i change the face image in the panel?

---

### Post by mcduck on 2009-02-16
System/Preferences/About Me, just click the picture frame in the top left corner and find any image you like.

Or alternatively just save picture of your choice as ~/.face

---

