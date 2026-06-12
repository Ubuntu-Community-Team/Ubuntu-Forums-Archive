---
title: "amarok not playing streams"
date: 2005-11-13
forum: Desktop Environments
---

### Post by karl_kashofer on 2005-11-13
Hi !

Today installed kubuntu on my lombard powerbook and am really impressed.
KDE looks good and the apps are much better than the gnome ones.

There is one thing that bugs me though:
I got amarok working by installing amarok-xine. Now i can play .ogg files.
However, amarok refuses to play any of the ogg streams on this website:

[http://dir.xiph.org/index.php?sgenre=&stype=Ogg+Vorbis&search=](http://dir.xiph.org/index.php?sgenre=&stype=Ogg+Vorbis&search=)

Anyone any ideas ?
Cheers,
Karl

---

### Post by daller on 2005-11-15
I have the same problem, even in Amarok 1.3.5!

---

### Post by nrwilk on 2005-11-15
I had this problem with Amarok a few days ago, and mlomker suggested I try using the xine engine.

Completely works now.  I haven't found a stream it won't play since.

In fact, I'm now listening to a stream off that site you linked.  Thanks!

---

### Post by daller on 2005-11-15
I'm using the xine engine, but it doesn't work here...

...What a fool I am! - Since upgrading I haven't been able to choose Xine

My fault!

---

### Post by nrwilk on 2005-11-15
[QUOTE=daller]I'm using the xine engine, but it doesn't work here...

...What a fool I am! - Since upgrading I haven't been able to choose Xine

My fault![/QUOTE]

is it working now?

---

### Post by daller on 2005-11-15
[QUOTE=Fealos]is it working now?[/QUOTE]

No, because having amarok 1.3.5 seems to cause dependency-problems when installing "amarok-xine"

---

### Post by nrwilk on 2005-11-15
[QUOTE=daller]No, because having amarok 1.3.5 seems to cause dependency-problems when installing "amarok-xine"[/QUOTE]
Is there any reason to run that version over 1.3.1?  Because 1.3.1 works pretty well for me.  Maybe you could downgrade?

---

### Post by tikal26 on 2005-11-15
you need to do this
sudo dpkg -i amarok_1.3.5-0ubuntu0.1_i386.deb amarok-gstreamer_1.3.5-0ubuntu0.1_i386.deb( or whatever engine you chooce)
I think  that 1.3.5 is alot nicer than 1.3.1 youcan listen to podcast

---

