---
title: "Gnome panel Tooltips: 11.10 Classic Gnome"
date: 2012-04-28
forum: Desktop Environments
---

### Post by maya123ca on 2012-04-28
If you have reverted from Unity to Classic Gnome and are bothered by those Panel tooltips, here's how to get rid of them.

1) Open Nautilus with this command: sudo nautilus

2) Navigate to /usr/share/themes

3) Double click your current theme and then on gtk-3.0

4) Double click on settings.ini (it will open with gedit) and add this line:
   gtk-enable-tooltips = 0

5) Save the file

6) Go back to the desktop, click on Applications, System Tools, System Settings, Appearance. 

7) Select a different theme, wait a moment, then re-select your original theme. 

Your panel should now be free of tooltips. :p

---

