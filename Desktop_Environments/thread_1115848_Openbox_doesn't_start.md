---
title: "Openbox doesn't start"
date: 2009-04-04
forum: Desktop Environments
---

### Post by tmun52 on 2009-04-04
I was wondering what openbox was since compiz won't work on my computer. I installed it and everything, but when I select the option for GNOME/open box, I get a single window instead of the desktop. It says there was some kind of error, and showed the ~/.xsession-errors file. it some thing like

WARNING : unknown option --choose-session=openbox-session

I couldn't get the exact message because the xsession-errors file was overwritten when I restarted in metacity.

Just in case, here are the messages it gives right now.

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Window manager warning: Failed to read saved session file /home/taher/.config/metacity/sessions/10e38676a4502b514e123885283041912700000077690007.ms: Failed to open file '/home/taher/.config/metacity/sessions/10e38676a4502b514e123885283041912700000077690007.ms': No such file or directory
seahorse nautilus module initialized
Initializing nautilus-share extension

(gnome-panel:7899): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24

** (nautilus:7901): WARNING **: Unable to add monitor: Not supported
x-session-manager[7769]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Failure: Module initalization failed
starting HAL detection for ac adaptors...none found
evolution-alarm-notify-Message: Setting timeout for 36759 1238889600 1238852841
evolution-alarm-notify-Message:  Sat Apr  4 20:00:00 2009

evolution-alarm-notify-Message:  Sat Apr  4 09:47:21 2009

Throttle level is 0
```

Computer Specs:
Ubuntu 8.10
Dell Pentium 4600
Intel Pentium 4 Processor 2.8 GHz
768 MB RAM
ATI Radeon HD 3650 Graphics Card

---

### Post by tmun52 on 2009-04-05
Bump

---

### Post by tmun52 on 2009-04-06
bump

---

### Post by rekado on 2009-04-07
I'm on Arch64 and use Openbox without GNOME. To start Openbox I had to add following line in ~/.xinitrc

```
exec openbox-session
```

If there are any other lines starting with "exec" then just add # in front of them to comment the line. It might be that GDM (or whatever login manager you use) doesn't provide the correct argument "openbox-session" but instead provides "openbox" which in turn fails to start an openbox session.

Please try editing ~/.xinitrc and report back if it worked. As I'm not running Ubuntu I cannot test it, but it should be working. Please note that by changing the ~/.xinitrc file, you will log in to an openbox session every time you start X.

If this solution is not applicable please also have a look at:
[http://icculus.org/openbox/index.php/Help:GNOME/Openbox](http://icculus.org/openbox/index.php/Help:GNOME/Openbox)

Good luck and make sure to report back if it helped.
All the best,
Rekado

---

### Post by tmun52 on 2009-04-09
I'm so sorry for the late reply. I've got compiz to work on my computer and I've been using that. Anyway, I tried looking for the ~./xinitrc file, but it was nowhere to be found, but I was able to log into openbox by just running openbox on its own from the login screen. Thanks so much for your help; it's very much appreciated.

---

### Post by rekado on 2009-04-15
You're welcome!
I'm not so familiar with Ubuntu anymore since I moved to Arch, hence my answer was a bit blurry...
If you ever feel like learning more about configuration of your system just the way you want it to be, you should check out Arch. I think I've learnt a lot more about my system by configuring it manually.

---

### Post by scoon on 2009-04-28
Hey there, 

Did you get this figured out?  It seems that gnome gets set up for ubuntu, doesn't work well with other WMs.

Thanks.

---

