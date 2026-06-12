---
title: "How to get the panel completely transparent?"
date: 2010-12-17
forum: Desktop Environments
---

### Post by Toxicbits on 2010-12-17
Is there an easy way to get the entire panel be transparent? Is it a bug that the applets dont adjust?

Toxicbits

---

### Post by Frogs Hair on 2010-12-17
It doesn't look easy .  [http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html](http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html)

---

### Post by Kognit on 2010-12-17
If you say that only a part of gnome-panel becomes transparent and other part doesn't than you have to go to you gtkrc of your theme and comment the line when issues the panel background pictures. Than go to terminal and do a command: "killall gnome-panel".

---

### Post by Toxicbits on 2010-12-18
I'm using equinox from the PPA and cannot find a folder for it in my ~/.themes directory. 
Do you know where to find this file?

Toxicbits

---

### Post by mcduck on 2010-12-18
If you've installed the theme through package management, it's installed system-wide, not just for your own user account. You should find it in /usr/share/themes.

---

### Post by Toxicbits on 2010-12-18
Thanks, it worked perfectly

Toxicbits

---

