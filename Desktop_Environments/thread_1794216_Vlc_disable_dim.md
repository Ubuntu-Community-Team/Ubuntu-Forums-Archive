---
title: "Vlc disable dim"
date: 2011-06-30
forum: Desktop Environments
---

### Post by daghost on 2011-06-30
Hi, is it possible to disable screen dimming while VLC is running? Because it keeps dimming my screen after 10 minutes while I am watching a movie without moving a mouse..

---

### Post by ajgreeny on 2011-06-30
I don't know what power-manager kde uses, but I have found it necessary in Lubuntu using xfce4-power-manager, to use the following command to start vlc ```
killall xfce4-power-manager && vlc && xfce4-power-manager
```which stops the power manager, opens vlc, then when vlc closes it starts power-manager again.

vlc manages to stop the screensaver starting, but has no similar effect on the power-manager as far as I can see.  However, this rather clunky work-around fixes it, but there may be better ways that I've not found.

---

