---
title: "xfce4 panel doesnt show"
date: 2005-11-18
forum: Desktop Environments
---

### Post by liquid boy on 2005-11-18
i installed xfce4. i loaded nautilus and saved session (so i could have desktop icons and stuff)

the xfce panel randomly stoped loading. so all i got was the window list (at the top) and nautilus (on the desktop) 

i tried a "completely uninstall" and reinstalling it, but it hasn't worked. when i type "xfce4-panel" into a terminal, i get the following error

```

(xfce4-panel:9262): xfdesktop-menu-WARNING **: xfdesktop: Could not locate a menu definition file

(xfce4-panel:9262): xfdesktop-menu-CRITICAL **: desktop_menu_parse: assertion `filename != NULL' failed
Segmentation fault

```

what the heck?

---

### Post by aysiu on 2005-11-18
[It's not looking good for you.](http://www.google.com/search?hl=en&q=xfdesktop-menu-WARNING+**%3A+xfdesktop%3A+Could+not+locate+a+menu+definition+file&btnG=Google+Search) I'm sorry.

---

### Post by videodrome on 2005-12-08
If I remember correctly. Navigate to the /home/~/.cache/sessions directory and rename the directory "sessionsbak." log out. log back in. fixed. delete old renamed sessionsbak directory.

---

