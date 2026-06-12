---
title: "Gnome i3 Upstart initctl and xgd..."
date: 2014-05-27
forum: Desktop Environments
---

### Post by raghav-9 on 2014-05-27
Hi, I've been playing with 14.04 for a few days and so far so good. I've just managed to get i3 window manager and gnome to work nicely so am very happy. But along the process I've come across something that has a little confused about how things work.

One of the problems I had was that indicator-power did now show in the indicator applet when starting an i3 session. It did show when starting a gnome fallback session or unity...

This is my /usr/share/gnome-session/sessions/i3-gnome.session:

```

[GNOME Session]
Name=i3-gnome
RequiredComponents=gnome-panel;unity-settings-daemon;i3-gnome;nautilus-classic;gnome-flashback-services;
DesktopName=Unity

```

And this gnome-fallback.session
```

[GNOME Session]
Name=GNOME Flashback (Metacity)
RequiredComponents=gnome-panel;unity-settings-daemon;metacity;nautilus-classic;gnome-flashback-services;
DesktopName=Unity

```

Both call gnome-flashback-services.desktop, which has the following line:

```
Exec=/sbin/initctl emit indicator-services-start
```

And /usr/share/upstart/sessions/indicator-power.conf has the line:

```
start on indicators-loaded or indicator-services-start
```

Which works perfectly in the gnome fallback session, but the power indicator does **not** load in my i3 session.
I tried editing the .session file, removing DesktopName=Unity made the indicator show but gave other strange behaviour, even with gnome-settings-daemon instead of unity-settings-daemon.

I've been able to fix the problem for now by editing /etc/xgd/autostart/indicator-power.desktop and changing

```
NotShowIn=Unity
``` to ```
OnlyShowIn=Unity;GNOME;
```

But now in ~/.cache/indicator-applet-complete.log I get lots of messages like:

```
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
```

Sorry for the long preamble, hopefully you're still there, but my questions are:

1) How are the indicators being loaded in the fallback session? The xdg/autostart file had "NotShowIn=Unity" so i'm assuming the indicators are loaded with "initctl emit indicator-services-start"? Is metacity required for initctl to work?

2) In both sessions, sudo initctl list doesn't list any of the jobs from /usr/share/upstart/sessions? Does this mean something else is wrong and a whole bunch of stuff that's meant to be running isn't?

3) why are there xdg/autostart files for services as well as upstart session files?

4) how come unity shows a panel with indicators but the session file only loads unity-settings daemon and compiz? whats going on behind the scenes, how is everything being loaded?

Hopefully someone can explain how this fits together, I would really like to understand it.

---

