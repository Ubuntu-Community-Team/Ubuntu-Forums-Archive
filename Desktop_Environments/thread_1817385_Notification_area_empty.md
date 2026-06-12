---
title: "Notification area empty"
date: 2011-08-03
forum: Desktop Environments
---

### Post by green0eggs on 2011-08-03
Hi all.

I'm using 11.04 with the gnome-panel (i.e. I'm using a 'Classic Ubuntu' session).

I've been playing around with the gnome panel desktop (installed docky and a few other things) and I've somehow made the notification area empty... there's definitely one on the panel but there are no icons in it. No nm, power etc.

Also, I can't work out a how to connect to the wireless network here without the notification area thingamy.

Also (2) I can't work out how to turn composting back on (it was on... now it's off). Don't know how it happened. This all occurred at once.

```
compiz --replace
``` does not work.

Any suggestions and help would be super-appreciated.
Cheers

---

### Post by green0eggs on 2011-08-03
I've just run ```
 sudo nm-applet
``` from the terminal and that makes the applet re-appear but it won't allow me to connect to either wired or wireless network.

Also(#3), when I try and log in with a Unity session I'm told I don't have the hardware to support Compiz which is rubbish because compiz/unity was all working this morning.

Could this be an update thing?

---

### Post by Frogs Hair on 2011-08-03
You can restore the Gnome Panel applets to defaults by using the following command . ```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

You can also restore Compiz to defaults in Gnome With the following .
```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
sudo reboot

```

---

### Post by green0eggs on 2011-08-03
Hey Frogs, thanks for the help.

> **Frogs Hair said:**
> ```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

This has returned gnome panel to its original configuration but my notification area is still empty. I also can't get network applet to connect.

> **Frogs Hair said:**
> 
You can also restore Compiz to defaults in Gnome With the following .
```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
sudo reboot

```
Compiz still won't come back.  :-(

---

### Post by Frogs Hair on 2011-08-03
See this thread [http://ubuntuforums.org/showthread.php?t=1506720&highlight=network+applet](http://ubuntuforums.org/showthread.php?t=1506720&highlight=network+applet)
As for Compiz I don't know why it is not working after reseting it .

---

### Post by green0eggs on 2011-08-04
Yeah, I saw that thread.

I've tried most sensible things like
```
 sudo killall nm-applet && sudo nm-applet
```
and
```

 sudo service network-manager stop
 sudo service network-manager start

```
to no avail.

The other suggestions in that thread are just right click and add notification area to panel. I have a notification area in my panel, just with no icons in it.

---

### Post by mcduck on 2011-08-05
Most of those things actually are indicators now instead of notifications, so make sure you have the indicator applet in your panel.

---

