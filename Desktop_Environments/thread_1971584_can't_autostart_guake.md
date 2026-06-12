---
title: "can't autostart guake"
date: 2012-05-02
forum: Desktop Environments
---

### Post by Mr.Pytagoras on 2012-05-02
Hello

I have very strange problem, I want to use guake and want it to be started automaticaly when gnome starts however it just won't start.

I have tried to mark the start with login shell in guake preferences, didn't work
Created autostart file in ~/.config/autostart, also didn't work

The weirdest part is that my others application gnote starts normally and also I have a script that is launched properly, the only problem is with guake.

Any ideas how to fix it?  

Using Ubuntu 12.04, Gnome Shell

---

### Post by dmdelorme on 2012-05-02
i just added to the start up applications far right icon on top of screen  where you find system settings, update etc. click add then i believe it is in /usr/bin/ 

Easy Smaesy...

---

### Post by vutborg on 2012-05-03
I have the same problem with guake, which is added to startup applications. My other startup applications start just fine, when gnome starts.
I have a script placed in /usr/bin/ called guake, which does:
```

#!/bin/bash

GUAKEPATH="/usr/lib/guake"
PYTHONPATH="${PYTHONPATH:+$PYTHONPATH:}$GUAKEPATH"
PYTHON="/usr/bin/python"

exec -a guake $PYTHON -OO $GUAKEPATH/guake.py "$@"

```

any ideas?

---

### Post by Mr.Pytagoras on 2012-05-03
I have also managed to work around this with a little script
```

#! /bin/sh

sleep 15
echo guake started: $(date) >> guake.log
guake

exit 0
```

I realize that if my other apps stars normally then it has to be something with depencies, also when i was running KDE the guake didn't start at boot I figured that it was because notification-daemon, so my guess here is that when guake is running at autostart the notification isn't running. After putting that **sleep** in that script and setting the autostart entry to exec my script it works fine.

---

### Post by Wrigley on 2012-09-10
Also, as an alternative to sleeping, you could also disable the "Enable popup notifications on startup" checkbox in the Guake Preferences. I just did that, and now it starts swimmingly! :)

/wrigley

---

