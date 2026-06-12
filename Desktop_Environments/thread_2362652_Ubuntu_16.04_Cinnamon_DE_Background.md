---
title: "Ubuntu 16.04 Cinnamon DE Background"
date: 2017-05-31
forum: Desktop Environments
---

### Post by Redalien0304 on 2017-05-31
Have Ubuntu 16.04 Cinnamon DE Cannot change the background? the Background now is Grey/white background. When i log out or  restart it Briefly changes to my selected Background.

Thanks for any any help

---

### Post by Redalien0304 on 2017-06-01
Anybody plz?

---

### Post by #&amp;thj^% on 2017-06-01
Seen this also but my fix was making sure your default file browser is Nemo and not Nautilus.

To disable Nautilus from drawing the desktop icons by executing:

```
gsettings set org.gnome.desktop.background show-desktop-icons false
```

Log out and log back in and if you see two identical "files" icons in the unity launcher. Unlock the top one and lock the bottom one and move it to the top below the icon for the dash. Then allow nemo to draw the desktop icons for you:

```
gsettings set org.nemo.desktop show-desktop-icons true
```

Should be pretty straight forward on how to reverse the above:

---

