---
title: "E17 ROCKS!!! What all can it do?"
date: 2008-05-22
forum: Desktop Environments
---

### Post by |{urse on 2008-05-22
Okay, so I have e17 (i used to use enlightenment a couple yrs ago) and am hella pleased with it! I have all my shelves the way i want them, animated wallpapers on all four virtual desks and animated icons. what other cool stuff can i do with e17? For instance how do i get the gadgets independent from the shelves and resized? Is compiz/beryl not in the cards for e17? etc?

---

### Post by |{urse on 2008-05-22
also has anyone tried 3ddesktop + e17? (which for some reason is not in the repos for gutsy anymore)

---

### Post by |{urse on 2008-05-22
Okay verified, I have 3ddesktop running on E17 with this .deb
[http://packages.debian.org/etch/i386/3ddesktop/download]("http://packages.debian.org/etch/i386/3ddesktop/download")
However, It's only showing one workspace in 3dview? I'll try invoking nautilus the running it, just for giggles.


lol no go!

looks like e17's workspaces are defined differently than gnome/kde

> ** (nautilus:11453): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:11453): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:11453): WARNING **: Can not get _NET_WORKAREA

** (nautilus:11453): WARNING **: Can not determine workarea, guessing at layout

and on running 3ddesk i still get just one 3d workspace =/

Anyone have any ideas? This windowmanager rocks but needs 3d workspace switching to be a kde/gnome killer.

---

### Post by atomkarinca on 2008-05-22
It's still under heavy development so don't expect a lot from it but there are some cool things you can do. You can check out Bling:

```
sudo apt-get install emodule-bling
```

Under configuration you can load Bling and voila you get cool effects. Also you can have fire, snow and rain on your desktop:

```
sudo apt-get install emodule-flame emodule-rain emodule-snow
```

And last thing, instead of GDM you can use prettier Entrance. I'm using OpenGEU so I don't know which command works for this on E17-cvs but it should be like this:

```
sudo apt-get install entrance
```

(It was opengeu-entrance-themes on OpenGEU :))

---

### Post by justin whitaker on 2008-05-22
Talk to Rui Pais. He should be able to help.

---

### Post by |{urse on 2008-05-22
Yeah i've already bugged the hell out rui lol. I do like entrance though, pretty snazzy. If only there were 3d desktop switching =(

---

### Post by atomkarinca on 2008-05-23
> **|{urse said:**
> Yeah i've already bugged the hell out rui lol. I do like entrance though, pretty snazzy. If only there were 3d desktop switching =(

I don't care for most of the compiz plugins but something like the scale plugin would be awesome.

---

### Post by |{urse on 2008-05-24
yes it definitely would be awesome. I don't exactly need or want the cube. Just something a little more 3d than fade in fade out or wipes.

---

### Post by worldwithoutgurus on 2008-05-25
Did you try ecomorph ?

See it in action:
[http://pourunmondesansgourou.ifrance.com/Videos/Ecomorph.ogv](http://pourunmondesansgourou.ifrance.com/Videos/Ecomorph.ogv)
(...couldn't make the cube work)

Ecomorph howto:
[http://code.google.com/p/itask-module/wiki/Stuff](http://code.google.com/p/itask-module/wiki/Stuff)

---

### Post by |{urse on 2008-05-26
Very cool! Looks like expose or that flip3d thing, I was looking on compiz's site and saw a few ppl that have made their cubes into globes, pyramids, etc. 
this is cool too but just like a simple 3ddesktop effect like 4 rotating desktops (not a cube) would be perfect as it uses very few resources. If anyone reading this knows how to make 3ddesktop recognize e17's workareas plz let me know.

---

