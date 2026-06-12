---
title: "KDE4 Multiple monitors (nvidia)"
date: 2008-05-18
forum: Desktop Environments
---

### Post by ubuntme on 2008-05-18
I have recently installed kubuntu 8.04 amd64 KDE4.

It looks great but is a little buggy, and I had problems getting multiple monitor behavior the way I wanted.

Firstly, the taskbar has a habit of disappearing when playing with settings, I'm not sure why, but to fix this:
```
rm .kde4/share/config/plasma*
```

And restart the X-server with ctrl + alt + backspace.

The second problem was that the taskbar was limited to one display, I wanted it spanned across both displays. 

First you want to make sure you have the nvidia drivers:

```
sudo apt-get install nvidia-glx-new nvidia-kernel nvidia-settings
```

Then configure xorg.conf:

```
nvidia-xconfig
```

Restart the X-server with ctrl + alt + backspace.

This should get the nvidia drivers working, though the taskbar will be limited to one screen.

To stretch it across both screens, open /etc/X11/xorg.conf and uncomment the following line in :

```
sudo nano /etc/X11/xorg.conf
```

Change 

```
#Option    "NoTwinViewXineramaInfo" "true"
```
to
```
Option    "NoTwinViewXineramaInfo" "true"
```

A side effect of this is that the log on screen is now spanning the two monitors, to fix this, You can change position of the login box under system settings.

Due to another bug, to do this you need to run:

```
sudo /usr/lib/kde4/bin/systemsettings
```

Unfortunately, the behavior is now such that windows maximize across both monitors.   The solution to this is to undo the above xinerama option! 

KDE3.5 dealt with this problem, windows would maximize across one monitor yet the taskbar could span the two monitors.  Any idea On how to deal with this problem in KDE4?

---

