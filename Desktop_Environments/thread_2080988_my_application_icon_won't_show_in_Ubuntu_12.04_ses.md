---
title: "my application icon won't show in Ubuntu 12.04 session fallback mode"
date: 2012-11-05
forum: Desktop Environments
---

### Post by nelson777 on 2012-11-05
I have a Python application that shows a systray icon, but it  just won't appear in Ubuntu 12.04 session fallback mode (Gnome Classic  WITH effects). It appears in 10.04, and in 12.04 with Unity. The problem is just in  Gnome Classic.
  I've already set:
  gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
  and I installed indicator-applet-complete but Alt-Win-right click won't work
  Anyone has any idea what can be wrong ?

---

### Post by ibjsb4 on 2012-11-05
Have you tried Alt + right click?

Look in /usr/share/applications to see if you have a start icon for your Python app.  If so, drag it to the panel.

If not, you should be able to create one in your main menu with alacarte.

---

### Post by nelson777 on 2012-11-05
I think I didn't explain the problem correctly, sorry. I meant that the systray icon won't appear, not the application in the menus.

Tried ALT-righ click. Won't work either;

---

