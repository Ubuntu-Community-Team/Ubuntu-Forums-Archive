---
title: "startup script help"
date: 2009-11-01
forum: Desktop Environments
---

### Post by akahige on 2009-11-01
I run several apps from Startup Applications. Because they have problems if they start too quickly, I created bash script launchers with sleep timers in them.

Unfortunately, this doesn't really work reliably and I'm wondering if there's not a more sophisticated way of being able to tell if the desktop is fully loaded before triggering the load command.

Anyone have any ideas?


Running Karmic AMD64 / Gnome.

---

### Post by VCoolio on 2009-11-02
I have this script from somewhere that checks if compiz is done and then starts conky. Maybe this can help you:

```
#!/bin/bash
until [ "$done" = "true" ]
do
if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
then
DISPLAY=:0.0 conky -c /home/symlinked/Conky/conkymain >/dev/null 2>&1 &
#DISPLAY=:0.1 conky -c /home/symlinked/Conky/conkymain >/dev/null 2>&1 &
done="true";
else
echo "CONKY IS WAITING"
done="false"
sleep 5;
fi
done
exit 0
```

---

### Post by akahige on 2009-11-02
Thanks for posting this.

I don't know if gnome-toolbar component would respond to the repeated DBUS calls the way Compiz does. (I don't know that it won't, either.)

Also, I found in a discussion that was related to the script that you posted, that there's apparently a Gnome feature that is supposed to finish loading the desktop before firing load-app-on-startup requests -- to prevent just this sort of problem. There's a patch filed against it for Compiz (that's so far been ignored), but supposedly Metacity should work. (Even though it doesn't.)

I guess there's just more bugs to be worked out.

---

