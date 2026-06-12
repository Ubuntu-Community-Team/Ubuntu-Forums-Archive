---
title: "kwin crashed and now desktop looks bad"
date: 2011-07-21
forum: Desktop Environments
---

### Post by st0kes on 2011-07-21
I had a major Kwin crash and could not recover from it. I had to Ctrl+Alt to another tty and reboot. After reboot my plasma desktop is a mess. The 'Desktop' files thing on my desktop has a thick grey border around it. And the bottom panel looks terrible, things just aren't being rendered properly. Any ideas how to recover from this? Image of the panel is below

[http://ukstokes.com/images/panel_gone_bad.png]("http://ukstokes.com/images/panel_gone_bad.png")

---

### Post by enimeizoo on 2011-07-21
Did you try to mv the .kde directory and reboot, to see if it is just some bad files the user directory? It is the easiest way to reset plasma. You could also look for plasma-specific files, but there are a lot. 
The easiest way to recover if you haven't tweaked kde a lot is probably to just remove your .kde directory and tweak it again.

---

### Post by inobe on 2011-07-21
it looks like a graphics card issue and your screen res is very low because of it.

why not adjust to the native monitors resolution?

---

### Post by schnelle on 2011-07-22
Probably kwin config file got corrupted. 

Delete ~/.kde/share/config/ [COLOR="Red"]kwinrc[/COLOR] file and then alt+f2 and type [COLOR="Red"]kwin --replace[/COLOR]

---

