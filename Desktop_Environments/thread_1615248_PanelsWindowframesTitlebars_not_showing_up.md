---
title: "Panels/Windowframes/Titlebars not showing up"
date: 2010-11-06
forum: Desktop Environments
---

### Post by riku88 on 2010-11-06
Hey,
I am running Ubuntu 10.10 with Gnome Desktop, and I was messing around with the number of virtual desktops when everything froze up, and then all my title bars dissapeared. I tried typing metacity into the terminal, it didn't work - it gives me the error:
```
metacity:ERROR:core/prefs.c:2495:meta_prefs_get_workspace_name: assertion failed: (workspace_names[i] != NULL)
Aborted
```
. I also tried to get into compiz-config, but it freezes up as soon as I open it. I tried restarting, and now my panels are gone too.
Next I tried to open up xorg.conf, but when I did it was blank. I had previously tried backing it up with this:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_<<20101106>>
```
but after I used it, the terminal just sat there blank and didn't do anything. I found out later that I actually do not have a xorg.conf file.
I have no idea what to do from here.
Any ideas? I don't want to lost my customizations - it took me a while to set up my panels. D:

Thanks in advance,
-Chris

---

