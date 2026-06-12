---
title: "How to toggle screen lock via script?"
date: 2008-06-07
forum: Desktop Environments
---

### Post by TheAmigo on 2008-06-07
I have a script that auto-detects my location at boot time (laptop that I use in different places).  Based on my location, I make several customizations (e.g. running BlueProximity & synergy or not).

If I'm at work, I want the screen saver to lock my screen, but when I'm at home, I don't want it to (although I do want the screen saver to run).

What I'd like to do is find a command-line way to un/check the gnome-screensaver-preferences' box for "Lock screen when screensaver is active".

Any suggestions?

I'm running Hardy with a close to default gnome desktop (including compiz).

---

### Post by Forlong on 2008-06-07
```
gconftool-2 -s -t bool /apps/gnome-screensaver/lock_enabled true
```
```
gconftool-2 -s -t bool /apps/gnome-screensaver/lock_enabled false
```

---

### Post by TheAmigo on 2008-06-08
Thanks, that's exactly what I was hoping existed.  I'll have to read up more on gconftool and see what else it does that I may want to use.

---

### Post by arpad9 on 2008-07-20
And for those that may not get the implications of this, here is a nice, simple bash script that toggles based on current state.  I associated this with an application launcher and put it in my panel... now I just have to figure out how to change the icon based on state. [edit: instead I found "xmessage" and added some lines]

```
#!/bin/bash

foo=`gconftool --get /apps/gnome_settings_daemon/screensaver/start_screensaver`

if [ $foo == 'true' ]
then
    gconftool --type=bool --set /apps/gnome_settings_daemon/screensaver/start_screensaver false
    xmessage -timeout 2 -center screensaver OFF
else
    gconftool --type=bool --set /apps/gnome_settings_daemon/screensaver/start_screensaver true
    xmessage -timeout 2 -center screensaver ON
fi

fi
```

---

### Post by arpad9 on 2008-07-20
Huh.  It's changing the keys but the screensaver seems unaffected.

---

### Post by arpad9 on 2008-07-21
Could be because I was editing the wrong keys!!

```

#!/bin/bash

foo=`gconftool --get /apps/gnome-screensaver/idle_activation_enabled`

if [ $foo == 'true' ]
then
    gconftool --set /apps/gnome-screensaver/idle_activation_enabled --type=bool false
    xmessage -timeout 2 -center screensaver OFF
else
    gconftool --set /apps/gnome-screensaver/idle_activation_enabled --type=bool true
    xmessage -timeout 2 -center screensaver ON
fi

```

---

