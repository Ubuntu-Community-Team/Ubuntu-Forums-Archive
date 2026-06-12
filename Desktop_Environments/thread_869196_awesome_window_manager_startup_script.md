---
title: "awesome window manager startup script"
date: 2008-07-24
forum: Desktop Environments
---

### Post by teepark on 2008-07-24
here's my file /home/travis/projects/config/startup_awesome.sh:

```
#!/usr/bin/env sh

awesome &
sleep 1 # wait before anyone tries to use awesome
/home/travis/projects/config/awesome_clock.sh &
/home/travis/.fehbg &
xscreensaver &
stalonetray -t --sticky --skip-taskbar --geometry 112x32+1166+766 &
sleep 1 # wait before anyone tries to use stalonetray
gnome-power-manager &
nm-applet
```
the problem is that stalonetray doesn't start up correctly - it shows up in the taskbar and isn't sticky (it only shows up in one tag). but this problem only occurs when first booting up. If I 'killall stalonetray' that drops me out of awesome entirely (don't quite understand that either), then when I start it up again stalonetray behaves the way it's supposed to.

I feel like I'm doing something wrong with the startup script.

for completeness:

awesome 2.3.2
slim 1.2.6
Xorg 1.4.0.90

---

### Post by pyre on 2009-10-31
I know this is an old post, but I'll reply just for future people coming here. [Came across this from a Google search]

When writing a startup script for X.org/X11/XFree86/etc the X session dies when your script dies. In this case, he started all of his apps in the background except for the last one (nm-applet), so his X session will die (dropping him back to a terminal or xdm/gdm/kdm login screen) when nm-applet exits. Killing stalonetray causes nm-applet to die because there is no longer a systray active for it (triggering the death of the X session).

Normally the thing that you use at the end of your startup script to keep the session open is the window manager, in this case 'awesome'.

So instead of launching awesome at the beginning and tossing it into the background to continue loading things, he should be launching it last.  If there is something that you need to load *after* the window manager is active you can use a delayed backgrounded sub-shell to do this. Ex:

```

(
  sleep 5
  stalonetray &
  sleep 1
  nm-applet &
) &
exec awesome

```

In this case, everything in the parens is run in another instance of bash (which the final & tosses into the background) which sleeps for 5 seconds before loading things. By the time the 5 second delay is over, awesome has (presumably) finished loading and everything the sub-shell launches will have a window manager already running.

---

