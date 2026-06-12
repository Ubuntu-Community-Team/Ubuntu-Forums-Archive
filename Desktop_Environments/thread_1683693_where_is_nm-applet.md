---
title: "where is nm-applet?"
date: 2011-02-07
forum: Desktop Environments
---

### Post by genjix on 2011-02-07
It's definitely running- it even connects when I restart but I cannot see it.

Must have deleted something while re-arranging my panel.

I add notification area and just get a tiny square,
[img]http://img17.imageshack.us/img17/1139/screenshotty.png[/img]

If you look closely you'll see 3 small squares (I've added 3 notification areas to show you). Even on reboot nothing appears in them.

---

### Post by genjix on 2011-02-08
bump

---

### Post by nogger on 2011-02-08
Try changing the colour of your panel (so you can see what's up there more clearly) and removing all instances of the nm-applet. Then add one back.

Worked for me - I'd somehow got three of them up there and none of them displayed correctly.

---

### Post by genjix on 2011-02-08
Hey,

I tried that but didn't work... By chance I did:
> killall nm-applet
nm-applet
And then it appears!

But not on reboot? Any ideas?

wtf... This Ubuntu release has been very bug prone for me. :p

---

### Post by Frogs Hair on 2011-02-08
Try reseting panels to defaults .```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by genjix on 2011-02-08
Thanks, I used that and found the problem.

I had set my window manager to awesome,
gconftool-2 --type string --set /desktop/gnome/session/required_components/windowmanager awesome

Seems GNOME + awesome don't work together... :(

---

