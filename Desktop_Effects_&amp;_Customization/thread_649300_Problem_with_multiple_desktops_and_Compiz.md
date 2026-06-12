---
title: "Problem with multiple desktops and Compiz"
date: 2007-12-24
forum: Desktop Effects &amp; Customization
---

### Post by talltex02 on 2007-12-24
Here is my problem: [http://i2.photobucket.com/albums/y39/TallTex02/6a8892f3.jpg](http://i2.photobucket.com/albums/y39/TallTex02/6a8892f3.jpg)
When I have Compiz window manager enabled, multiple desktops go crazy. As you can see in the screen shot, I have one desktop selected on the panels manager, but my taskbar shows two.

Thanks in advance.

---

### Post by argie on 2007-12-25
The same thing happens to me. Compiz takes over your virtual desktop manager. You'll have to change the settings for Compiz.

In CompizConfig Settings Manager:
General Options » Desktop Size » Here you can change Horizontal or Vertical Viirtual Size.

---

### Post by Zorael on 2007-12-25
KDE's pager Kicker applet is notorious for not working well with Compiz.

To get it to at least semi-work, add the argument "--ignore-desktop-hints" to your script that starts Compiz. At least then you'll get the correct number of desktops, but the pager applet will remain useless. I just removed it and learned to use the Expo plugin. Which rocks.

```
zorael@azrael:~$ cat /usr/bin/compiz.start
#!/bin/bash

# kill adept_notifier since it bugs out
killall adept_notifier

# invoke compiz with [COLOR="DeepSkyBlue"]KDE[/COLOR] and [COLOR="Lime"]Nvidia[/COLOR] tweaks. [COLOR="DarkOrchid"]pass arguments to compiz[/COLOR] and [COLOR="DarkOrange"]leave terminal control to the user[/COLOR]
[COLOR="Lime"]__GL_YIELD="NOTHING"[/COLOR] compiz [COLOR="Lime"]--loose-binding[/COLOR] [COLOR="DeepSkyBlue"]--ignore-desktop-hints[/COLOR] ccp [COLOR="DarkOrchid"]$@[/COLOR] [COLOR="DarkOrange"]&[/COLOR]

# sleep for 10 and restart adept_notifier
sleep 10
adept_notifier &
```

---

### Post by yesint on 2007-12-28
I've just noniced the same problem with the number of desktops in my fresh kubuntu 7.10 install. 
I also have a problem with rotating cube - it is flat (two-sided) even if the number of the desctops is > 2.
I wonder why compiz works just perfect with KDE in Mendriva 2008, but not in Kubuntu. In Mandriva the pager applet behaves as it should and the cube is rotating the desktops nicely, so these problems **can** be solved. Anybody knows if it possible to clone the settings from Mandriva to kubuntu somehow? I really don't want to switch to gnome...

---

### Post by lewisskinner on 2007-12-28
I had the same problem.  Essentially it's a matter of confusing *desktops* (which are a K/Ubuntu item) with *Viewpoints* (the Compiz item).  One K/Ubuntu desktop may have up to 32 viewpoints.  Or that's how I read it.

Although oddly enough, when I first installed Compiz, I could use the desktop switcher to switch Compiz viewpoints (with the zoom/transparency etc working).  Weird or what?

---

### Post by yesint on 2007-12-29
I've checked the settings in Mandriva. In Compiz the horisontal size of the desctop is 4, vertical 1, number of desctops 1. Probably this will work, but I didn't try because I uninstalled Kubuntu ;) I can't connect to the wireless network with Kubuntu, but can with Mandriva, so I switched to Mandriva now. This is also a bit weird for me because the wireless driver seems to be the same in both distros...

---

