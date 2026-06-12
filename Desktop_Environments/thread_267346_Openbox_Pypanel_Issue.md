---
title: "Openbox: Pypanel Issue"
date: 2006-09-28
forum: Desktop Environments
---

### Post by kalbir on 2006-09-28
I was running Pypanel fine until I decided to mess about with the colors in the pypanelrc config file, now I get the following message:

/usr/lib/python2.4/site-packages/Xlib/display.py:30: DeprecationWarning: Non-ASCII character '\xf6' in file /usr/lib/python2.4/site-packages/Xlib/protocol/display.py on line 750, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details
  import protocol.display
Traceback (most recent call last):
  File "/usr/bin/pypanel", line 957, in ?
    PyPanel(display.Display())
  File "/usr/bin/pypanel", line 98, in __init__
    self.loop(self.display, self.root, self.window, self.panel)
  File "/usr/bin/pypanel", line 818, in loop
    self.updateTasks(dsp, root, win, panel)
  File "/usr/bin/pypanel", line 774, in updateTasks
    self.setIcon(t)
  File "/usr/bin/pypanel", line 314, in setIcon
    icon.path = ICON_LIST["default"] or "/usr/share/pypanel/ppicon.png"
KeyError: 'default'

Any ideas as to what is wrong?

Kalbir

---

### Post by croak77 on 2006-09-28
Do you still have the default /etc/pypanelrc or was that the one you were messing with? Try purging and then reinstalling.

---

### Post by moore.bryan on 2006-09-28
[I]i'm with croak... compare your backup with the changed .pypanelrc
the first line of your error seems to tell you there's a "not allowed" character in your .pypanelrc
[/I]

---

### Post by kalbir on 2006-09-28
I was going to overwrite the altered file with the original but then thought of something different- I tried replacing the hex color values with some that only used numbers in the hex code rather than alphanumeric values and everything worked again. I'm not sure why this should make a difference (especially since some of the defaults had "f" in them) but it did!

Thanks for the help!

Kalbir

---

### Post by kerry_s on 2006-09-28
Could i see a screenshot of your openbox setup?

I'm using openbox too, right now i'm trying it with konqueror. I'm thinking of a trying minimal install and using konqueror as the filemanager,webrowser,image viewer,...I've installed to see exactly what just installing konqueror brings with it that i can use instead of installing other things that konqueror can do already. Example: installing konqueror you also get the kicker, so now there's no need to install a panel, because it's there.

---

### Post by K.Mandla on 2006-09-28
> **kerry_s said:**
> I'm using openbox too, right now i'm trying it with konqueror. I'm thinking of a trying minimal install and using konqueror as the filemanager,webrowser,image viewer,...I've installed to see exactly what just installing konqueror brings with it that i can use instead of installing other things that konqueror can do already. Example: installing konqueror you also get the kicker, so now there's no need to install a panel, because it's there.
Hey, quit posting those screenshots. I drool on myself every time I see them.

[[IMG]http://img172.imageshack.us/img172/8772/screenshot2sf1.th.jpg[/IMG]](http://img172.imageshack.us/my.php?image=screenshot2sf1.jpg)

:mrgreen:

---

### Post by kerry_s on 2006-09-28
Sorry, I just can't help myself. I just figuered out konqueror also brings kdesktop, so i can use that to set my background from kcontrol and it gives me tranparency in the panel and menu.

---

### Post by kalbir on 2006-09-29
I'm using Openbox on my pretty old laptop (1.0Ghz, 32Mb Ram, essentially no graphics card!) so for me it is a way of keeping the resource usage down. I'm away from home for about a week though so I won't be able to post a screenshot right now but I'll do it as soon as I get back. 

This thread

[http://www.ubuntuforums.org/showthread.php?t=248486](http://www.ubuntuforums.org/showthread.php?t=248486)

often has openbox screens in it though!

Kalbir

---

