---
title: "Menu entries missing"
date: 2004-12-30
forum: Desktop Environments
---

### Post by drag on 2004-12-30
Ok, I went thru synaptic and installed a few dozen games. Now when I go to play them I can't find them anywere in any of my application menus.

I am normally a Debian user and I assumed that it would work out the same way, if I can't find a program in the normal gnome menu I go down to the debian menu and find it their, then I can simply drag the item up to the task bar and that's were I go to get it.

I tried running update-menus and such, but that didn't make a difference. 

Of course the menu entry to open up the nautilaus file browser (I like to have spatial mode for desktop stuff, but have browser mode aviable for other things) was missing completely, so I built that manually on the taskbar. I looked at places and they said to open up applications:// in the nautilaus browser, but that didn't work.

But I have all these programs installed and the only way I can run them is to open up a terminal and run them by name, and I can't even remember the name of half the programs I installed!

So how do I set it up so that when I install a program I can have it be added automaticly to my menus?  

I realy like having the Debian-style menus, so how to I get that back?

One of the biggest pet pieves is having to muck around with menus, it's so boring....

Oh, and I am using hoary.

---

### Post by ulrich on 2004-12-30
hi,
as far as i know ubuntu didnt use debian-menues.
so theres a good chance of installing some app and dont have any menu entries.
its a real annoyance not having menu entries made automagically.

though im using warty , hitting Ctrl + L  and opening 'applications:///' in nautilus works flawlessly. maybe theres some bug in hoary which will go with the next update...

---

### Post by drag on 2004-12-30
[QUOTE=ulrich]hi,
as far as i know ubuntu didnt use debian-menues.
so theres a good chance of installing some app and dont have any menu entries.
its a real annoyance not having menu entries made automagically.

though im using warty , hitting Ctrl + L  and opening 'applications:///' in nautilus works flawlessly. maybe theres some bug in hoary which will go with the next update...[/QUOTE]

Ya. It's something that's different in hoary. They are using Gnome 2.9, I guess, and the gnome people are trying out adhering to freedesktop.org menu-spec standards.

---

### Post by varunus on 2004-12-30
The "Debian" menu is in Hoary Hedgehog.  (Or the development version, at least.)  So hopefully they'll keep it for the release.

Other desktop environments, like XFCE, have access to the debian menu even under Warty though.  For now, you can just edit applications:// to add your games, I guess.  Most stuff still added itself to the menu, from what I saw before I went to Hoary.

---

### Post by drag on 2004-12-31
Maybe something is broken for me, then.

I am tried doing the applications:// thing in nautilus and it always says that the location does not exist. When I do a different one, like fonts:// it works.

If that works for you, then not me, then it could be a bug with the PowerPC build or something like that. It's on my Apple laptop. 

So I would like to know if that is suppose to be working, then if it is suppose to work like that, then I'll file a bug report or something of that nature.


Otherwise it sounds like I'll have to use XFCE. Not a big deal. I like XFCE, too. Docks are a bit annoying, but whatever.  ;)

....

Is there a way to run XFCE's menu in Gnome? To bad I don't have my laptop right now...

---

### Post by drag on 2005-01-01
Well I figured out what happenned. 

In order to get the debian-style menus you have to install the menu-xdg package.

thank goodness that's now working.

Now can anybody tell me how to get my trash back on the desktop...

---

### Post by taygan on 2005-01-07
Even with the broken menus in hoary you can add a desktop entry by manually creating a file in /usr/share/applications..  just check out some that are in there already as templates..

---

### Post by jbh on 2005-01-08
you can also just create a launcher on the desktop, configure it and stick it in the toolbar in hoary.

---

