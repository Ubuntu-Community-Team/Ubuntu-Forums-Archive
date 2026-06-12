---
title: "Xgl/Compiz with Big Desktop fglrx 2 x 1280x1024"
date: 2007-07-24
forum: Desktop Effects &amp; Customization
---

### Post by leohart on 2007-07-24
Has anyone managed to get Compiz (Xgl) running on a two monitor setup (two 1280x1024) using fglrx (Big Desktop settings).

Any clue, suggestion, links would be really appreciated.

---

### Post by synthaxx on 2007-07-25
I tried, for days, and failed. 
If you like a challenge you can try it using a second startxgl script that's run on the second head, but i couldn't get this to work reliably. This was a couple of months ago though, so maybe it'll work for you.

I'll post the exact scripts when i get home so you can have a go.

p.s. I can really suggest looking into the open source ati drivers (if they work for your card), installed them yesterday, and i've been running compiz without any major problems since then. I highly recommend them.

---

### Post by synthaxx on 2007-07-25
Here you go.

I made some additions to the startxgl.sh:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
startxgl2 &
exec dbus-launch --exit-with-session gnome-session
```

And added a startxgl2.sh

```
#!/bin/sh
unset SESSION_MANAGER
Xgl :2 -display :0.1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:2
exec dbus-launch --exit-with-session gnome-session
```

Like i said, i never really got this to work right, but it did give 2 different xgl sessions (with beryl at the time).

Maybe you can expand on this.

---

### Post by sperlyjinx on 2007-10-30
Anyone have any luck with this, now that fglrx supports AIGLX?  I have a dual 1280x1024 panels and am having a problem setting up compiz.  I can get it to run, but the screen is jumbled.  Any help would be appreciated.  Thanks!

---

