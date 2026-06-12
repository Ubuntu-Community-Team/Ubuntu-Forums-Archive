---
title: "screensaver applet?"
date: 2009-05-07
forum: Desktop Environments
---

### Post by Crowder on 2009-05-07
I know there is an applet to inhibit suspend and hibernate, but sometimes I just want to turn my screensaver off for movies etc.. Simple enough to do, but I'm not so fond of having to go through the menus every time, especially because I usually forget to change it back! :icon_frown:

does anyone know of an applet i can put on the panel to easily inhibit the screensaver in just a click or two?

thanks in advance.

---

### Post by CoolHand on 2009-09-10
I stumbled across your question while searching for the same thing.  Have you found a solution yet?

If not I will share my workaround.  I have a script I wrote that I call gscontrol.  I simply call the script with the argument stop or start to turn on or off the screensaver.  If you want to use it just save it in an executable file and name it as you wish.  Here is the script:

```

#!/bin/bash
#
# Small script to turn on or off my
# screensaver and screen lock
#
# Simple start stop stuff from here
start() {

	gnome-screensaver &

}

stop() {

	killall gnome-screensaver

}

restart() {
	stop
	start
}

# See how we are called.
case "$1" in
  start)
	start
	;;
  stop)
	stop
	;;
  restart)
	restart
	;;
  *)
	echo $"Usage: $0 {start|stop|restart}"
	exit 1
esac

exit $RETVAL


```

You can also point to this from a manually added button to make it work easier.

---

### Post by gimspang on 2011-09-24
I use Power Manager Inhibit Applet 2.32.0 on Natty.
[http://www.gnome.org/projects/gnome-power-manager/](http://www.gnome.org/projects/gnome-power-manager/)
You can get it from Synaptic

---

### Post by Frogs Hair on 2011-09-24
If you are using the Gnome panel and not Unity the inhibit applet was on the add to panel menu found by right clicking the panel .

---

