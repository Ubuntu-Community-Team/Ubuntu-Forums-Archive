---
title: "How to disable transparant terminal in some themes?"
date: 2010-07-04
forum: Desktop Environments
---

### Post by vangop on 2010-07-04
Hi!
On some themes (like dust sand) the terminal goes transparent. 
I checked the profile, and it has a solid color settings, so this must have been changed from somewhere else and I can't get rid of the stupid transparency.
Please advice how to turn this off, terminal is barely usable when I can see my browser through it.
Thanks!

---

### Post by 55 62 75 6E 74 75 6D 65 on 2010-07-04
Open a terminal. Go to edit. Create a new terminal profile, or edit the default. Go to background. Change the transparency settings ...etc. Hope this help. (for gnome terminal)

---

### Post by khuttger on 2010-07-04
You could try Alt+F2 then type in gconf-editor and go to (/ > apps > gnome-terminal > profiles > Default) and look through that :)

Hope it helps.

---

### Post by vangop on 2010-07-04
Thanks!
Both answers worked, /apps/gnome-terminal/profiles/Default/use_theme_background gconf value is used to turn off per-theme settings. 
The other way is to use "transparent background" in the profile settings and manually set transparency to 0

---

### Post by khuttger on 2010-07-04
Good deal. Glad you got it fixed.

---

