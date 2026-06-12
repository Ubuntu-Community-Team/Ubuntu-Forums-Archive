---
title: "Jaunty sound muted after boot"
date: 2009-05-12
forum: General Help
---

### Post by bubbawv on 2009-05-12
I'm working off of a new installation of Ubuntu.  I can boot into Gnome or Xfce desktop manager.  Regardless of which 80% of the time I boot I find that the PCM on the alsamixer is muted and the volume is also turned completely down.  I can manually turn it back up and everything works.  However I can not get the settings to stay.

Does anyone have any ideas?

---

### Post by Fipi on 2009-05-23
I have the same problem. Does anyone know a fix for this?

---

### Post by fillintheblanks on 2009-05-23
you could try maybe these work..
0 to 100 for volume level, and bunch of different channels I'm not sure what all there names are these are some of them

> amixer sset 'PCM Center' 50

> amixer sset 'Master' playback 50


if so, you could make so they run automatically on startup everytime. just an idea

---

### Post by Akegata on 2009-05-31
I have the same issue, and I've tried unmuting it at startup (through .fluxbox/startup).
However, apparently there's a stranger issue here, because a few minutes after I've logged in, the master channel gets muted again. After manually unmuting it after that, it never gets muted again though..

If anyone has any ideas about what's going on I would be a happy camper. This is really annoying.

---

### Post by sabre2th on 2009-06-08
Same thing happens on my laptop.  I recall it also happening with a previous install (probably Intrepid, but I don't remember).  I managed to get it working back then, but I haven't figured it out yet this time around.  It might not be the same problem; I'm not sure.

---

### Post by davidmohammed on 2009-06-08
I had a similar issue.  The following works for me:
create a file called soundstartup using a terminal session
```

gedit soundstartup
```

add the following code by copying and pasting here

```
#!/bin/sh 

sleep 5

/usr/bin/amixer -c 0 sset Master,0 unmute > /dev/null

/usr/bin/amixer -c 0 sset Master,0 95% > /dev/null

```
 and save when exiting gedit.

type in the terminal window
```
chmod +x soundstartup
```
 run soundstartup from your sessions manager (system - preferences - sessions)

:D

---

