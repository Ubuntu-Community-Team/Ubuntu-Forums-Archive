---
title: "compiz failing on me!"
date: 2007-12-07
forum: Desktop Effects &amp; Customization
---

### Post by twist2b on 2007-12-07
at first it was all fine.... but then it would freeze on compiz startup....
NOW i completely removed and reloaded.... and it gets this:

[PHP]:~$ compiz --replace & gtk-window-decorator --replace &
[1] 9821
[2] 9822
craig@craig-laptop:~$ /usr/bin/compiz.real: Couldn't load plugin 'glib'
inotify_add_watch: No such file or directory
/usr/bin/compiz.real: Couldn't load plugin 'vpswitch'
/usr/bin/compiz.real: Couldn't load plugin 'mblur'
/usr/bin/compiz.real: Couldn't load plugin 'crashhandler'
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"




[/PHP]
help? thanks

---

### Post by mouseboyx on 2007-12-07
try 
```
sudo apt-get remove [COLOR="Red"]--purge[/COLOR] compiz
```


[COLOR="Red"]--purge[/COLOR] means it deletes all config files so you should start with a fresh install when you install compiz again.

---

