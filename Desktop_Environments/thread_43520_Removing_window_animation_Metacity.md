---
title: "Removing window animation Metacity"
date: 2005-06-22
forum: Desktop Environments
---

### Post by Lunde on 2005-06-22
Does anybody know how to remove the strange animation that apper when you open a window in Gnome / Metacity?

I know you can use the gconf-editor to check

apps > metacity > general > reduced_resources

But this also gives a wireframe when moving the window.

---

### Post by felipe on 2005-06-22
what animation? i can only think of that - admittedly not beautiful - window-border-zooming-animation which shows when minimizing a window

...and i'm pretty sure that can't be disabled singularly.

---

### Post by Lunde on 2005-06-22
[QUOTE=felipe]what animation? i can only think of that - admittedly not beautiful - window-border-zooming-animation which shows when minimizing a window

...and i'm pretty sure that can't be disabled singularly.[/QUOTE]
 I'm sure it can, I found some place on the net telling that by editing one of the .c files it could be done.

I know there are no easy solutions to this, just checking if there are someone who knows the hard way. It's not really that important to me, just nagging me a bit sometimes.

---

### Post by Dave_is_sexy on 2005-06-22
Agreed, i'd like rid of it too

---

### Post by FLeiXiuS on 2005-06-22
There's only a simple fix available.  I made a thread on this a bit earlier in the year but here we go.  I'll restate my self because I'm lazy to use to the quick search :-P.

Applications > System Tools > Configuration Editor

From here open:

Apps > Metacity > General

Scroll down till you see reduced_resources.  Place a check in the box to the right.  Voila.  That'll do it for you.

---

### Post by felipe on 2005-06-28
uh, ok i was talking about disabling it via gconf, not by editing the sources...

interesting anyway

---

### Post by Lunde on 2005-06-28
[QUOTE=felipe]uh, ok i was talking about disabling it via gconf, not by editing the sources...

interesting anyway[/QUOTE]
 Yeah! would be nice if somebody knew where this was located in the source

---

### Post by vbgunz on 2005-11-02
If you want to get rid of that ugly animation and get rid of the wireframes at the same time go to > System > Preferences > Assitive Technology Support & Enable Assistive Technologies...

It's not really an answer but it is a workaround I found to work nicely... I would settle with the wireframe *IF* the wireframe mode was a bit more cusomizable... It is currently not to taste... Good luck!

---

### Post by Alexander Kirillov on 2005-11-03
[QUOTE=Lunde]Yeah! would be nice if somebody knew where this was located in the source[/QUOTE]
You better ask the same question in the metacity mailing list: 
[http://mail.gnome.org/mailman/listinfo/metacity-devel-list](http://mail.gnome.org/mailman/listinfo/metacity-devel-list)
or in gnome desktop-devel-list: 
[http://mail.gnome.org/mailman/listinfo/desktop-devel-list](http://mail.gnome.org/mailman/listinfo/desktop-devel-list)

---

