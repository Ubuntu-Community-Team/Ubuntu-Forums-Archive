---
title: "Can somebody explain to me what this xgl script does?"
date: 2007-09-07
forum: Desktop Effects &amp; Customization
---

### Post by shaggy999 on 2007-09-07
```
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

What do the 'cookie' and 'xauth' lines do? And are they necessary? The reason I ask is because if I include those lines in my script gnome fails to load upon login (I just get a black screen w/ an error). If I comment those two lines out everything starts fine.

**UPDATE:** I got a bit of an answer here: [http://ubuntuforums.org/showthread.php?p=3326486#post3326486](http://ubuntuforums.org/showthread.php?p=3326486#post3326486)

---

### Post by pointone on 2007-09-07
The cookie and xauth lines are a simple hack that fixes an issue for some people where the restart and shutdown buttons are not visible when running an Xgl session. If you don't have this problem, you can safely comment out these lines.

> For those who are running Xgl nested, the reason why you lose the "shutdown/reboot/etc" options is because the Xgl server running at :1 isn't authorized to talk to GDM.

My (rather hacky) solution was to add the following to my Xgl startup script (just before running gnome-session):

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

This clones the xauth cookie from :0 into :1.

Let me know if this works for you; I've tried it on two systems now and it seems to work, at least when using GDM.

[http://sudan.ubuntuforums.com/showthread.php?t=244662&page=3](http://sudan.ubuntuforums.com/showthread.php?t=244662&page=3)

---

### Post by shaggy999 on 2007-09-07
Oh, that's interesting as I have that exact problem. I have no shutdown/restart options. But if I keep the code in there my xsession fails. :( Damn.

---

### Post by DaveRM on 2007-09-08
shaggy999,
I had the same problem.
I added a sleep 4 after the first line.
It works for me.

```
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
sleep 4
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

---

