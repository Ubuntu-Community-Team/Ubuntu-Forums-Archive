---
title: "Gnome Art Manager crashes"
date: 2006-06-20
forum: Desktop Environments
---

### Post by tdn on 2006-06-20
Hi.

Gnome Art Manager (the one that comes with the gnome-art package) crashes when I try to download Login Manager Themes.
It also crashes now and then. It seems random.

I have experienced this on three completely different hardware platforms and with three completely fresh installations of 6.06.

How do I fix this?

---

### Post by crazy___cow on 2006-06-21
I had the same problem. Try to install "ruby-gnome2" and its dependences (some ruby staff) to fix things.

---

### Post by Anduu on 2006-06-21
WOW you find the coolest stuff when you least expect it...didn't even know this existed :p 

Anywho it seems to be working fine on my box without ruby-gnome2 installed....hmmmm

---

### Post by Anduu on 2006-06-21
Ooops correction...try running it in a terminal...

```
gksudo gnome-art
```It works that way.

Trying to launch it from the menu crashes it for me.

---

### Post by crazy___cow on 2006-06-22
Gnome Art Manager requires Ruby, Ruby-Gnome2 an ReXML (librexml-ruby???) as you can see in the homepage of this cool project:

[http://www.miketech.net/gnome-art/](http://www.miketech.net/gnome-art/)

If you manually install this stuff the program starts to work quite well. Maybe the gnome-art package is broken and do not check for this dependences....

---

### Post by Anduu on 2006-06-22
OK I see what is going on...

Installing it through Synaptic gives only root permissions for writing so when it is asked to do something it gives a permission denied then quits.

That is why it works fine when launched via gksudo.

Actually I prefer to run it this way as no one else can monkey with my themes ;)

---

