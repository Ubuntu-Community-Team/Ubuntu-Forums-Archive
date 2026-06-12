---
title: "HOWTO (simple one) replace gnome-screensaver with xscreensaver."
date: 2010-05-12
forum: Desktop Environments
---

### Post by dE_logics on 2010-05-12
Although xscreensaver is much better and liked by many users, the Ubuntu devs replaced it with gnome-screensaver simply cause - 

1) It's integrates better with the gnome-desktop.
2) It follows release cycles of Gnome.

Since the devs and admins won't listen, we users have to clean their **** up and this is the howto - 

In Ubuntu, the gnome-screensaver is running; but xscreensaver is better, so we need to replace it. 

The gnome-screensaver runs as a daemon...removing this gnome-screensaver package will remove this executable also - 

```
apt-get remove gnome-screensaver
```

And install xscreensaver - 

```
apt-get install xscreensaver
```

Then start the xscreensaver executable to start the xscreensaver daemon.

```
xscreensaver -nosplash
```

xscreensaver-demo will show the xscreensaver's configuration dialog, the thing that you see in system>preferences.

Now that standby/suspend/screen off is controlled by gnome-screensaver and configured through the power manager(system>preferences), since it's disabled now, it won't work anymore, but other configuration (power button action etc...) will still work.

Configure your standby/suspend/screen off configuration form xscreensaver.

Next, you have to add the xscreensaver -nosplash at startup; to do so, goto system>prefferences>startup applications; there click add and after putting a name, add "xscreensaver -nospash" in the comand section.

To have all screensavers enabled - 

```
apt-get install unicode-screensaver xscreensaver-gl-extra rss-glx xscreensaver-data-extra
```

---

### Post by azertyh on 2010-05-13
hi,
i installed xscreensaver 2 hours ago. i did like you but through synaptic.

---

### Post by dE_logics on 2010-05-13
> **azertyh said:**
> hi,
i installed xscreensaver 2 hours ago. i did like you but through synaptic.

Yeah, it's the same thing.

You see synaptic is a front end to apt-get and apt-cache. But you should remove gnome-screensaver though to make the screensavers work properly.

---

### Post by wandalalakers on 2011-02-12
Thx, my screensavers in xfce stopped working and now they are back working because of your info!

> **dE_logics said:**
> 
Then start the xscreensaver executable to start the xscreensaver daemon.

```
xscreensaver -nosplash
```

Next, you have to add the xscreensaver -nosplash at startup; to do so, goto system>prefferences>startup applications; there click add and after putting a name, add "xscreensaver -nospash" in the comand section.

To have all screensavers enabled - 



---

### Post by John_T on 2011-02-15
> **dE_logics said:**
> 
...
Next, you have to add the xscreensaver -nosplash at startup; to do so, goto system>prefferences>startup applications; there click add and after putting a name, add "xscreensaver -nospash" in the comand section...

I just wanted to point out the "nospash" typo in that paragraph.  If you copy and paste from the wrong section of the message, as I nearly did, you'll get unexpected results.

Otherwise, great stuff, thanks!

---

### Post by omegamike3 on 2011-02-17
It appears that notify-osd will overlap xscreensaver, meaning while the screensaver is active, any notifications that you get will still show up. There's an open bug from October on launchpad, but it doesn't look like anyone has done anything with it. [https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/660224]("https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/660224") Has anyone else had this issue or know a way to fix it?

---

### Post by forestwalkerjoe on 2011-02-28
Ok.. so if the bug is still not fixed.. and i checked.. it's not. any one have any idea how to fully remove the XScreensaver and put back the sreensaver for Gnome? i tired to reverse the code above.. and i cant Tell Screen saver to start of X screen to stop.. got any ideas? I even removed the Start Daemon thing from Start up..

---

### Post by uriel1998 on 2011-03-07
Try ```
sudo apt-get purge xscreensaver unicode-screensaver xscreensaver-gl-extra rss-glx xscreensaver-data-extra
```

to remove everything from xscreensaver.  Then use synaptic to reinstall gnome-screensaver.  You may need to reinstall gnome-power-management as well and put gnome-screensaver in your startup.

[http://live.gnome.org/GnomeScreensaver](http://live.gnome.org/GnomeScreensaver)

---

### Post by Stormdancer on 2012-03-01
I really prefer the xscreensaver controls, but... I've gotta be able to lock my screen. Does this really mean I'm stuck with gnome-screensaver?

---

### Post by Krytarik on 2012-03-01
> **Stormdancer said:**
> I really prefer the xscreensaver controls, but... I've gotta be able to lock my screen. Does this really mean I'm stuck with gnome-screensaver?
Nope, please see this guide how to re-enable the lock screen :P :

[http://www.tuxgarage.com/2011/10/installing-xscreensaver-in-11-10-ubuntu.html](http://www.tuxgarage.com/2011/10/installing-xscreensaver-in-11-10-ubuntu.html)

Regards.

---

