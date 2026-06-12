---
title: "/apps/panel/applets/clock_screen0"
date: 2009-07-01
forum: Desktop Environments
---

### Post by rhdinah on 2009-07-01
Ref: Gnome ... gconf-editor

On the desktop version of Jaunty there is the key:

/apps/panel/applets/clock_screen0

In the Jaunty netbook remix there is no such key. I need it to be able to do a custom time format so I may add a hostname please.

Can anyone tell me where this information is now? It seems like everything is now based on schemas ... and these schemas are uneditable at this point ... but there must be an equivalent way.

---

### Post by Konrad Ansehelm on 2009-11-14
It's one of the applets indicated with a number. On my Ubuntu Netbook Remix 9.10 it was called 'applet_5'. You can see which one it is by clicking all the applets in /apps/panel/applets/ one by one and looking at the value of the bonobo_iid field. It's the one called 'OAFIID:GNOME_ClockApplet'.

---

### Post by kerry_s on 2009-11-14
in gconf-editor the best way to find the keys is to use "edit->find" it's the first thing i go for when using the editor.
for example: put "clock", check both boxes & click find.

---

### Post by rhdinah on 2011-03-02
Solution: don't use Netbook remix if you expect a 1:1 port of features.

---

