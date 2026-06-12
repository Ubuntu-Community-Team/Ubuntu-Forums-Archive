---
title: "[ASK] My Ubuntu Window Theme become ugly after change theme"
date: 2013-02-25
forum: Desktop Environments
---

### Post by hidayatkids on 2013-02-25
Hello ubuntu user,
I'm newbie on Ubuntu, and still like to try it.
Now i use ubuntu 12.10 version.
Last time after install gnome 3.6 , i try to change my theme to "Gnome-Cupertino"
but my Window Theme become look like classic and ugly.

This is the screenshoot.
[IMG]http://s7.postimage.org/ilxwf98h7/image.png[/IMG]

Is there is step that i miss ?
Please anyone recomendation what should i do to make it right..:-(

---

### Post by unheeding on 2013-02-26
I bashed my head against this the other day.  In order to get the window decorations in gnome-shell, I had to move my theme directory to /usr/share/themes/

Say your theme directory is ~/.themes/gnome-cupertino/

sudo mv ~/.themes/gnome-cupertino/ /usr/share/themes/gnome-cupertino/

Press Alt+F2, type "r", hit enter.  This restarts gnome-shell. Then reselect the theme in Gnome Tweak Tool.

---

