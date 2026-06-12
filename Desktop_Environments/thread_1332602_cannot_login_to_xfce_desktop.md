---
title: "cannot login to xfce desktop"
date: 2009-11-20
forum: Desktop Environments
---

### Post by clwillingham on 2009-11-20
OK i got a seriously annoying issue.

after spending some time playing with window managers, trying to find the one that my computer would do the best with while providing the best user interface. i eventually settled on xfce, and then found out that it couldn't connect to my windows network. so i did some researching and found [this]("http://ubuntuforums.org/showthread.php?t=304131&highlight=xfce+samba"). i got all the way to step 4 where it said to reboot, however when i rebooted, it started up with the usual xfce login screen, then i told it to login with xfce session, and thats where the problem started. i hit login and it started loading, then the screen blanked out for a moment, it came back, loaded a bit more, and brought me back to the xfce login screen so i tried 2 more times, failed each time, tried gnome and it worked. but i want xfce. what could have broken it? is security denying me access? or is it something else?](*,)

---

### Post by jeffus_il on 2009-11-20
Delete your .xsession-errors file from a console to zero the error log
reboot the machine 
run into your problem once
and post the .xsession-errors file (in your home folder)

---

### Post by clwillingham on 2009-11-20
well it started working again... no reason at all, it just started working

if you still want it though here is what the errors log said:
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/d$
/usr/bin/startxfce4: X server already running on display :0

** (gnome-screensaver:1431): WARNING **: Failed to get session presence proxy: Could$
xfdesktop[1454]: starting up

(polkit-gnome-authentication-agent-1:1489): GLib-GObject-WARNING **: cannot register$

(polkit-gnome-authentication-agent-1:1489): GLib-CRITICAL **: g_once_init_leave: ***$
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3

(xfce4-mixer-plugin:1477): libxfce4mixer-CRITICAL **: xfce_mixer_get_track: assertio$

(xfce4-mixer-plugin:1477): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_car$


```

EDIT

well it was working... now it stopped working again

---

### Post by jeffus_il on 2009-11-21
Someone else had the same problem in this thread:
[http://ubuntuforums.org/showthread.php?t=203877]("http://ubuntuforums.org/showthread.php?t=1016346")
that was way back in 2006
I don't know if it's relevant
and here:
[http://ubuntuforums.org/showthread.php?t=1016346]("http://ubuntuforums.org/showthread.php?t=1016346")
someone called curtistee found a solution to a similar problem
reply number 6 after his (5) was a solution

Hope this helps

---

