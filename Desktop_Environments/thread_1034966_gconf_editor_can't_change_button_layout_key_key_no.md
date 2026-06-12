---
title: "gconf editor can't change button_layout key: key not writable"
date: 2009-01-09
forum: Desktop Environments
---

### Post by jokoon on 2009-01-09
[IMG]http://zonas.free.fr/img/scr/gconf-not-writable.png[/IMG]
[IMG]http://zonas.free.fr/img/scr/edit-key.png[/IMG]
[IMG]http://zonas.free.fr/img/scr/read-only-front-confpath.png[/IMG]

I don't know why I can't edit this key (even in root!), I also see a "schemas" dir at the root of the gconf-tree, but it is quite annoying... I always edited this key to have a different button_layout, and now I can't change it anymore... what's wrong ?
I also tried to change this value, gconftool-2, but no such luck...

---

### Post by jokoon on 2009-01-12
Any clue ? I thought it was because I ran gconf-editor either with sudo or gksudo, editing root's settings, but it doesn't change anything : same error, key is not writable...

---

### Post by moore.bryan on 2010-02-07
Same here... wish I had searched a little more before I launched my own thread...

---

### Post by moore.bryan on 2010-02-12
The solution for this was some updated/triaged packages... this was a known bug, as per [https://bugs.launchpad.net/ubuntu/+source/ubuntu-netbook-default-settings/+bug/518626]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-netbook-default-settings/+bug/518626").

---

### Post by neocheema on 2010-04-26
How did you guys solve this issue? I've hit the same problem with ubuntu 9.10 as I find this key "not writable"
/apps/gnome-terminal/profiles/Default/background_image  

Which packages do I need to upgrade?

---

