---
title: "Move Chrome Window Controls in Gnome 3"
date: 2011-10-26
forum: Desktop Environments
---

### Post by 98cwitr on 2011-10-26
Since Gnome went back to the right side, and me trying to close Chrome actually brings up the Activity pane, I am trying to get the buttons back on the right side. Unfortunately, gconf-editor doesn't work anymore. Any pointers?

---

### Post by Alwimo on 2011-10-26
Does right-clicking on the top area of the window and selecting "use system titlebar" (or whatever it says) help?

---

### Post by Frogs Hair on 2011-10-26
Try this : ```
sudo apt-get install dconf-tools
``` I want to get my buttons to the left on the shell , but I have not tried yet .

---

### Post by zeroseven0183 on 2011-10-27
If you have gconf2 installed already, open a Terminal and type this
```
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"
```

That should set the buttons to the right. If it does not automatically move them, log out then log back in.

It worked for me instantly. I executed the command while my Chromium option is set to Use system title bar and borders then set the option to Hide system title bar and use compact borders.

---

### Post by 98cwitr on 2011-10-27
> **Alwimo said:**
> Does right-clicking on the top area of the window and selecting "use system titlebar" (or whatever it says) help?

That got it. Thanks!

---

