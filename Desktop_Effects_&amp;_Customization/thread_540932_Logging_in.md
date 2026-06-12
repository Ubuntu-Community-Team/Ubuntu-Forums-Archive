---
title: "Logging in"
date: 2007-09-02
forum: Desktop Effects &amp; Customization
---

### Post by TorontoStorm on 2007-09-02
I am having problems when I log in using a session called "GNOME with XGL" which runs the following script: 

```

#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

```

It never properly logs in, sometimes it gives me the error "Gtk-warning **: cannot open display:", other times my desktop does not load (meaning no icons and I can't right click), or sometimes avant-window-navigator does not start (it is in my session startup list). The only weird thing is that these problems happen one at a time, sometimes I don't get the Gtk-warning, sometimes my desktop does load, and sometimes avant-window-navigator does start. The 3 things I added to startup are Awn (avant-window-navigator), Compiz Fusion (compiz --replace), and Google Desktop Search (opt/google/desktop/bin/gdlinux start). Thanks for any help

---

### Post by steveneddy on 2007-09-02
I thought that you didn't have to call XGL in Feisty because of the fact that it is already enabled. Or maybe there was something like XGL that was enabled by default so you didn't have to call it to start at login.

That was one of the "features" of Feisty. When I upgraded to Feisty from Edgy, I lost my XGL file. It didn't need it anymore.

---

### Post by TorontoStorm on 2007-09-02
> **steveneddy said:**
> I thought that you didn't have to call XGL in Feisty because of the fact that it is already enabled. Or maybe there was something like XGL that was enabled by default so you didn't have to call it to start at login.

That was one of the "features" of Feisty. When I upgraded to Feisty from Edgy, I lost my XGL file. It didn't need it anymore.
Well, the reason I call XGL is because this guide says so : [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

---

