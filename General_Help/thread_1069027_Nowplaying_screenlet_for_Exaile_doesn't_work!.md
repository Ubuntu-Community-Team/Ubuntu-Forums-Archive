---
title: "Nowplaying screenlet for Exaile doesn't work!"
date: 2009-02-13
forum: General Help
---

### Post by neo_1in on 2009-02-13
I access internet through a proxy. For some reason the in built proxy option of exaile didn't work (for last.fm or plugins), so i use a script to launch exaile.
```
#!/bin/sh
export http_proxy=http://144.16.192.245:8080
dbus-launch exaile %f
```
The script works exactly as intended, but the Nowplaying screenlet and music applet of gnome-panel don't work with such instance of exaile, though they work fine with a normal instance (i.e. from application menu or run...).
Help !! ;)

---

