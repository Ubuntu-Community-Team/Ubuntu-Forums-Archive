---
title: "Gnome Classic (Effects) Died after Dconf Editor Install and Unity 24-h Time Config"
date: 2013-11-11
forum: Desktop Environments
---

### Post by pennrabb on 2013-11-11
I have been using 12.04 with gnome classic (with effects), this was working OK. I was trying to get the Indicator Applet to show 24-hour time, day of week and seconds. The time settings were already set to 24h in the gnome Time Settings area, but the applet was still showing 12h time.
I did some searching and found a thread here where someone advised to load Dconf Editor where the applet could be configured to show the seconds and day of week, that appeared to work OK. Then in the same thread a person advised that you could only change the time to 24-hour in Unity. I went to Unity, and sure enough, it was set 12-hour. I set it to 24. 
Then when I logged out and back in I found that when I tried to load the Gnome Classic desktop, it put me back to the Unity desktop.
Only Gnome Classic (No Effects) will load.
I reverted all the time settings to default and tried uninstalling dconf editor and reinstalling gnome, but no change. Looks like I will have to reinstall 12.04 to get my desktop back. Any ideas of what I can kill off and reinstall before I do that?

---

### Post by ibjsb4 on 2013-11-12
Hi pennrabb, welcome to the forums :)

I really do not see any connection with clock settings/dconf and your login problem with classic + compiz.  You can of course hose your install by playing around with other dconf settings, but I can't see clock settings doing that.  So me thinks something else is going on.

Since your using compiz (I do not) have you tried resetting it?
```

dconf reset -f /org/compiz/
```

And on a side note ..

Dconf-editor is much improved these days, but in Gnome I find gconf-editor still having its uses.  I find myself going to the both of them.

[http://ubuntuforums.org/showthread.php?t=2146728](http://ubuntuforums.org/showthread.php?t=2146728)

If you wish to go ahead with a reinstall it is not necessary to do a complete reinstall.  Just reinstall the classic desktop.

```
sudo apt-get install --reinstall gnome-session-fallback
```

---

### Post by hamishmb on 2013-11-13
You could either use the instructions above, or you could install MATE desktop, which is also pretty close to Gnome 2 :)

---

### Post by stinkeye on 2013-11-13
The unity interface is only a plugin for compiz.
The **gnome-classic (with effects)** session also uses compiz as the window manager.

I've had occasions where the unity plugin has become 
enabled in the **gnome classic (with effects)** session
after doing something in unity.

Log into the **gnome-classic (with effects)** session and open a terminal.
Check you are in the gnome-classic session....
```
echo $DESKTOP_SESSION
```

Then use compizconfig-settings-manager (ccsm) to disable the unity plugin.
May need to install compizconfig-settings-manager.

If gnome-panel isn't showing after disabling unity, in the terminal run...
```
gnome-panel & disown
```

If compiz fails to reload properly during any of these steps, run..
```
compiz --replace & disown
```

---

