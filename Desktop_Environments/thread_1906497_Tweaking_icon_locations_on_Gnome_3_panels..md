---
title: "Tweaking icon locations on Gnome 3 panels."
date: 2012-01-09
forum: Desktop Environments
---

### Post by Trapper on 2012-01-09
U11.10 and Gnome 3

Okay, is there some special maneuver for moving icons around on the panel? In Gnome 2 you could simply move your icon to wherever and just lock it in place. In Gnome 3 whenever I move something it pulls a student body right/left/center maneuver and doesn't allow me to place it where "I" want it. Movement seems to be full right, full left or center but nowhere in between.

---

### Post by prusswan on 2012-02-09
seems to annoyingly intended, interesting how there are no replies

---

### Post by prusswan on 2012-02-10
is there some kind of plugin or config settings to override the default behavior?

---

### Post by Frogs Hair on 2012-02-10
There is no way to move the icons in Unity . If you are using the Gnome  fall-back session you can take a look at the link .[http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html](http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html)

The fall-back session was supposed to be temporary and eventually removed ,so it doesn't have many features . I have read that Alt+Right Click allows some panel function in the fall-back session .

---

### Post by bradleypariah on 2012-06-26
Sorry to bump a slightly old thread, but the question was never answered, so I see no point in kicking up the topic again elsewhere and cluttering up the forum.

There were answers provided about Unity and Gnome fallback, but the OP was asking about repositioning icons in the Gnome 3 panel.

It surprises me that there are 15 pages of extensions at [https://extensions.gnome.org/](https://extensions.gnome.org/) and I can't seem to find a single entry about freedom to reorganize the panel.  Have I missed it?
No joke, a Google search pops up ***nothing***, save this thread that's missing an answer.

I realize restriction is one of the big complaints people have about Gnome3, but I'm actually starting to get acclimated to it.  I just want to move a couple things around.

Can anybody help?  I've looked in /home and /etc and opened every file within any folder with the word "gnome" in it.  None of those files seem to configure the layout of the panel.  Where should I look?  This can't be impossible.  I'm just too much of a noob to figure it out on my own.  :confused:

---

### Post by Frogs Hair on 2012-06-26
All the Ubuntu desktops on 12.04 run on top of Gnome 3.4. So the identification of the specific desktop environment is needed to find an answer. The Gnome Shell like unity is some what locked down other than what is possible with extensions. There are extensions that allow the user to hide or move some items , but not all items . Many extensions were developed by users with a particular need.

---

### Post by Bobhuber on 2012-06-26
> **bradleypariah said:**
> Sorry to bump a slightly old thread, but the question was never answered, so I see no point in kicking up the topic again elsewhere and cluttering up the forum.

There were answers provided about Unity and Gnome fallback, but the OP was asking about repositioning icons in the Gnome 3 panel.

It surprises me that there are 15 pages of extensions at [https://extensions.gnome.org/](https://extensions.gnome.org/) and I can't seem to find a single entry about freedom to reorganize the panel.  Have I missed it?
No joke, a Google search pops up ***nothing***, save this thread that's missing an answer.

I realize restriction is one of the big complaints people have about Gnome3, but I'm actually starting to get acclimated to it.  I just want to move a couple things around.

Can anybody help?  I've looked in /home and /etc and opened every file within any folder with the word "gnome" in it.  None of those files seem to configure the layout of the panel.  Where should I look?  This can't be impossible.  I'm just too much of a noob to figure it out on my own.  :confused:
  
/usr/share/gnome-shell/js/ui/panel.js

---

### Post by lolpenguin on 2012-06-26
It is possible in GNOME Shell, but to have a button specifically where you want it requires annoying tweaking regarding Clutter, the panel's children, and the three *Box'es.

---

### Post by bradleypariah on 2012-06-27
> **Bobhuber said:**
> /usr/share/gnome-shell/js/ui/panel.js
I'll give it a look.  Thanks!

> **lolpenguin said:**
> It is possible in GNOME Shell, but to have a button specifically where you want it requires annoying tweaking regarding Clutter, the panel's children, and the three *Box'es.

[img]http://oyster.ignimgs.com/wordpress/write.ign.com/64763/2012/04/what-is-this-i-dont-even-spiderman.jpg[/img]

---

### Post by szrobert on 2013-01-07
L Windows + L ALT + R Click on the icon, then choose move from menu  ... work on ubuntu 12.10 !

---

