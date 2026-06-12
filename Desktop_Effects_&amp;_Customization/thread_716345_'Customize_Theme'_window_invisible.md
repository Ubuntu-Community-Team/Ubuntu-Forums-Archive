---
title: "'Customize Theme' window invisible"
date: 2008-03-05
forum: Desktop Effects &amp; Customization
---

### Post by flowevd on 2008-03-05
hi

when i go to gnome appearance and select customize theme i am presented with the window border and an empty white box. clicking around in the box changes the panels as it would if they were visible, but only one may be clicked on at a time and then you must alt-f4 back out and return until you click the correct one.

very annoying. anyone know what can i do?

---

### Post by flowevd on 2008-03-06
anyone?

---

### Post by FuturePilot on 2008-03-06
Close the Gnome Appearance Properties and try this
```
sudo apt-get remove --purge gtk-qt-engine
```
Then try opening the theme preferences.

---

### Post by flowevd on 2008-03-06
brilliant, it worked.

thanks a lot.:)

---

### Post by FuturePilot on 2008-03-06
No problem :)

---

