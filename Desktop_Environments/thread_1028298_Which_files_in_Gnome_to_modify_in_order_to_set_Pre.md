---
title: "Which files in Gnome to modify in order to set Preferences manually?"
date: 2009-01-02
forum: Desktop Environments
---

### Post by Vpc on 2009-01-02
I have Ubuntu 8.04. I would like to modify Preferences directly rather than through the System menu in Gnome. I would like to modify/write scripts to:
1) launch gnome-terminal on start up as when I do that via the System->Preferences->Sessions it appears without a title bar so I am unable to move the terminal
2) to change the idle time for the screen saver so I can just execute a script rather than setting it via System->Preferences->Screensaver (as I change it daily to run a video for news in the morning and then decrease the idle time again after it's done)

Does anyone know which files/settings have to be modified in order to do the above?

Thanks.

---

### Post by PhrankDaChickenGeek on 2009-01-02
1)
This probably doesn't work b/c the window manager or some other item has not started before the terminal. Maybe create a script that waits a few seconds before starting the terminal

2)
```

$ gconftool-2 --set "/apps/gnome-screensaver/idle_delay" --type int X

```
where X is the amount in minutes

---

### Post by Vpc on 2009-01-03
Thanks for the info. 

1) More on gconf:
[http://www.gnome.org/~bmsmith/gconf-docs/C/gnome-screensaver.html](http://www.gnome.org/~bmsmith/gconf-docs/C/gnome-screensaver.html)

2) Where would you launch the script you suggested?

---

