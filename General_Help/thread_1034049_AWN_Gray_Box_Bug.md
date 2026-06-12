---
title: "AWN Gray Box Bug"
date: 2009-01-07
forum: General Help
---

### Post by The_Orig on 2009-01-07
I installed AWN from the repositories today and all went splendid for a little while. Every so often one of my icons gets a gray box over it that is the exact width of the animated icon and the exact height of it's animation "summit". The gray box goes away if you hover your mouse of the icon affected, causing it to animate.

The animation I'm using is squish, although, the bug persists if I use zoom as well. The gray box is always over my weather icon, so I removed the weather icon to see if it was just that specific icon, but sadly the gray box just moved over. Fiddling with what applets I had simply effected what applets got the dreaded "gray box" and how large it was (the separator was also affected).

I did a Google search and Ubuntu forums search for relevant problems, but I didn't' find any so I figured I'd make my own post.

I've attached a picture of the bug and a picture without the bug.


EDIT: I've also installed ALL dependencies for EVERY applet, but the problem persists.

EDIT2:

So..... it turns out the bug existed, BUT not under the name "Gray" or "Box". All other bug reports were filed under "artifacts" or "white" and weren't revealed when I searched for previous bug reports >.<!

Anyway, the problem was resolved when NVidia released a newer driver version; simply install the NVidia drivers version 180.08 or newer and then restart and ALMOST all of the "artifacts" should be fixed.

If you can't install the newer driver version one hackish fix someone found was to move your applets to the left side of your dock and the launcher to the right. This seemed to have mixed results.

Here is the link to the bug report on launchpad:
[https://bugs.launchpad.net/awn/+bug/273326](https://bugs.launchpad.net/awn/+bug/273326)

---

### Post by The_Orig on 2009-01-10
bump

---

### Post by andrewsomething on 2009-01-10
Run avant-window-navigator in a terminal and paste any output here.

---

### Post by The_Orig on 2009-01-11
Nothing interesting :(


```
Screen is composited.
APPLET : /usr/share/awn/applets/cairo_main_menu.desktop
APPLET : /usr/share/awn/applets/separator.desktop
LOADED : /usr/share/applications/firefox.desktop
LOADED : /home/bretton/.local/share/applications/alacarte-made-1.desktop
LOADED : /usr/share/applications/gnome-system-monitor.desktop
LOADED : /usr/share/applications/rhythmbox.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/share/awn/applets/separator.desktop
APPLET : /usr/share/awn/applets/weather.desktop
APPLET : /usr/share/awn/applets/calendar.desktop
APPLET : /usr/share/awn/applets/awnnotificationdaemon.desktop
The following is an informational message only: 
notification-daemon: no process killed
First attempt failed:  The following is an informational message only: 
notification-daemon: no process killed
['/usr/share/awn/applets/calendar', '/usr/lib/python2.5', '/usr/lib/python2.5/plat-linux2', '/usr/lib/python2.5/lib-tk', '/usr/lib/python2.5/lib-dynload', '/usr/local/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages/Numeric', '/usr/lib/python2.5/site-packages/PIL', '/usr/lib/python2.5/site-packages/gst-0.10', '/var/lib/python-support/python2.5', '/usr/lib/python2.5/site-packages/gtk-2.0', '/var/lib/python-support/python2.5/gtk-2.0', '/usr/share/awn/applets/calendar/google']

```

---

### Post by The_Orig on 2009-01-20
bump :(

---

### Post by phantom3113 on 2009-01-20
I'm interested in any help with this as well. Although the problem isn't as bad on mine, my applet(s) will *occasionally* turn into a grey box. It only ever happens when I close an open window and the bar shrinks down to get rid of the empty spot; the icon, normally for the trash applet, turns into a grey box while sliding and then comes back when done.

---

### Post by rafaeliga on 2009-01-30
im interested on this too..any news ?

---

### Post by psilocybin2 on 2009-01-30
i had same problem, along with little black lines showing up covering the icons..part of the reason i moved to cairo,

---

### Post by jreyes33 on 2009-02-02
I thought it was a not so common bug! I also have it. Any help would be really useful

---

### Post by psilocybin2 on 2009-02-02
the problem will probly be addressed in a future update, for now your going to have to live with it or switch to another dock

---

### Post by The_Orig on 2009-02-03
Incorrect, the problem wasn't even an AWN problem but a problem with the video drivers. See my original post.

---

### Post by The_Orig on 2009-02-03
I guess it's not quite clear that I edited the original post.

The problem has been SOLVED. Read the edit sections of the original posts to see the answers and link to the bug forum.

---

### Post by Crafty Kisses on 2009-02-03
Oh ok thanks! I was having a similar issue, really weird.

---

