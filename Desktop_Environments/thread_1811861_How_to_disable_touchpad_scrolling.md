---
title: "How to disable touchpad scrolling"
date: 2011-07-25
forum: Desktop Environments
---

### Post by SteveDee on 2011-07-25
I need to disable touch-pad vertical edge scrolling on a laptop running Lubuntu.

There must be a config file somewhere, but I have not been able to find it.

Ideas anyone?


Edit: Sorry, just found the answer. In terminal: synclient VertEdgeScroll=0

---

### Post by LogansRun22 on 2012-03-05
When I do this in Ubuntu 11.10 with LXDE (so Lubuntu basically), it's not persistent. I have to do it every time I log in or power on. Does anyone know how to actually save this so it sticks every time?

---

### Post by Shannondorf on 2012-03-24
@LogansRun22,

You could write the command found by SteveDee at the end of /etc/rc.local , so that it is executed at each startup. You can append it to the file with:

```
sudo echo "synclient VertEdgeScroll=0" >> /etc/rc.local
```

EDIT: Forget what I just said, you're going to have to edit the /etc/rc.local file manually with root permissions, because there's an "exit 0" that needs to stay at the end.

---

### Post by SteveDee on 2012-03-25
> **LogansRun22 said:**
> ...Does anyone know how to actually save this so it sticks every time?

I think the cleanest way to do this on Lubuntu (and possibly LXDE) is first to create a script like this:-
```

#!/bin/sh
#Disable touch-pad vertical scrolling
synclient VertEdgeScroll=0

```
...save as (say): disVScroll.sh and set executable.

Now create a .desktop file (e.g. DisableVScroll.desktop) and enter something like this:-
```

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=/home/steve/disVScroll.sh
Name=DisableVScroll
Icon=

```

Now save to: /etc/xdg/autostart

When you restart and go to: Preferences > Desktop Session Settings
you should see DisableVScroll listed, so you can enable/disable this feature from here.

Notes:-
 you'll need to run as root for some of those operations.
 your script probably needs to be saved in /usr/bin rather than your home dir (as shown).

---

