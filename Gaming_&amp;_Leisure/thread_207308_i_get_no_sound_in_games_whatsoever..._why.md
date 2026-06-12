---
title: "i get no sound in games whatsoever... why?"
date: 2006-07-01
forum: Gaming &amp; Leisure
---

### Post by Polygon on 2006-07-01
its really making me mad, i cant play any games in linux cause for some reason, sound refuses to work

it used to work in americas army, but then it stopped

doom3, quake4, warsow, americas army, nothing.

but i will say that in games like doom3/quake 4, i get sound but its really distorted and it sounds really bad and static like.

my sound card was auto configured by ubuntu, and normal sound (like mp3's and gnome sounds) work perfectly.

any help?

---

### Post by dipswitch on 2006-07-01
I have no sound at all. It used to work. But doesn't anymore. I hate linux.

---

### Post by Footissimo on 2006-07-01
For Doom 3 / Quake 4 try adding ```
+set s_driver oss
``` to the end of the command (i.e. doom3 +set s_driver oss, or whatever).

Not sure about AA or Warsow - run them from a terminal and paste out anything that looks suspect..others may be able to help more..also specs, Ubuntu version and that sort of thing :)

---

### Post by Polygon on 2006-07-01
for some reason americas army works again... very weird but whatever it works, i wont touch it

and that fix for quake 4 works! thanks a lot.

---

