---
title: "Ubuntu Slowness"
date: 2007-03-09
forum: Desktop Environments
---

### Post by Raeth on 2007-03-09
I've been using Ubuntu on-and-off since Hoary, and always notice a certain latency of the graphical interface, right up to Edgy 6.10.

I feel menus take a split-second longer to open, buttons a split-second longer to depress, tabs take a half-second to switch, and GTK windows noticably redraw themselves from blank-white when I alt-tab to them.

A few things have been suggested:
1. You're running slow hardware, or you should install the prop. 3D drivers for your vid card.
2. GTK is just slow.
3. There is no latency, you're seeing things, Ubuntu's GNOME is fine.

I have some refutements to these, and lastly some hard evidence to support my claim.

1. My specs are basically "AMD 64 3200+, 1024 MB DDR RAM, 256 MB Radeon X850 XT", which should be overkill for rendering some beige, 2D buttons :D
As for 3D drivers, I can install ATi's FGLRX drivers and have working 3D without problem, and the latency persists regardless with or without the prop. drivers.

2. This may be so, but it doesn't explain why my friends' installations of Ubuntu (GNOME) run sweetly and snappily. It also doesn't explain why ported GTK apps such as Gaim run faster on Windows than my Ubuntu. The menu items, buttons, everything, react with an unnoticable delay.

3. I'm not one to underestimate the power of perception, so I thought my problem required some evidence (as proof to myself as much as anyone) that Ubuntu's GNOME was slow.
I found a GTK benchmarking program [http://gtkperf.sourceforge.net/](http://gtkperf.sourceforge.net/) which works by performing a bunch of widget-tasks (pressing buttons, selecting selection boxes etc) a set number of times.
I went with the default benchmark of 100 repeats, chose a bunch of desirable GNOME themes and picked up a Debian live CD running GNOME 2.14 as my test piece.

The number is the time (seconds) in which it took to perform the entire benchmark, so **the lower the better.**

```
              Ubuntu  Debian
No change:    19.10   16.22
Clearlooks:   22.25   16.22
Raleigh:      14.85   10.62
SmoothGNOME:  17.69   12.76
Ubuntulooks:  23.50   18.94
```

So my question is, with that information in mind, why on earth is GNOME on Ubuntu so slow?

---

### Post by kanha on 2007-03-09
strange ! generally ubuntu is faster than debian everywhere i used

---

### Post by tpdasf on 2007-03-12
I had the same problem, even though my hardware is a lot worse than yours. A week ago I accidentally uninstalled basically most of the default ubuntu and gnome applications so I was forced into using KDE. All of a sudden everything was fast again! I reinstalled all the ubuntu apps and everything stayed fast. I don't know if one of those apps had a conflict or was corrupted before, but it seemed like uninstalling and reinstalling did the trick

---

### Post by jwalker on 2007-03-12
I am in full agreement with the thread starter. I have seen GNOME running nicely, on dual core machines with a nice amount of RAM. But this 'latency' on lower end machines drives me crazy! For a few reasons I tried KDE, and I now run Kubuntu on my lappy and GNOME at home on my desktop. I blame my desktop for having a Celeron. But that's probably not it. It is strange, you launch Nautilus and that will take longer then it should when opening, but once it's up it is pretty quick when browsing your drive. 

Anyway, I too would be curious about this, and IMO KDE is faster. I wish KDE didn't have such a dumb name, I like it so much more than GNOME. Not that GNOME is a bad *** name at all either...

Anyway, yes, boooo! Things take too long to open in GNOME.

---

### Post by Raeth on 2007-03-15
> **jwalker said:**
> I am in full agreement with the thread starter. I have seen GNOME running nicely, on dual core machines with a nice amount of RAM. But this 'latency' on lower end machines drives me crazy! For a few reasons I tried KDE, and I now run Kubuntu on my lappy and GNOME at home on my desktop. I blame my desktop for having a Celeron. But that's probably not it. It is strange, you launch Nautilus and that will take longer then it should when opening, but once it's up it is pretty quick when browsing your drive. 

Anyway, I too would be curious about this, and IMO KDE is faster. I wish KDE didn't have such a dumb name, I like it so much more than GNOME. Not that GNOME is a bad *** name at all either...

Anyway, yes, boooo! Things take too long to open in GNOME.

When I say GNOME is slow, I mean once it's loaded into memory. Apps start fast enough, it's the interface I find latent- opening menus, switching between windows, minimising/maximising...

Yeah, KDE is faster for me too, at least in terms of widget-latency.

---

### Post by stojic on 2007-03-16
I recently installed Edgy and was also wondering why it's slower than my Debian installation. Then, during some fiddling, I disabled CPU Frequency manager (under System -> Administration -> Services) and suddenly everything became fast and snappy.

I am running it on laptop and it seems that frequency manager simply isn't responsive enough to speed up CPU during such small task as opening menus or resizing windows. It speeds up CPU during some more intensive tasks such as Blender rendering, so it's functioning well. On desktops CPU Frequency manager is probably disabled by default, so that's why Ubuntu might be faster there.

You can try turning it off as well, the only drawback is more heat and shorter battery life, but you can always turn it on when on battery (no need for reboot or logout when turning it on/off). I use laptop mostly at home so this is a non-issue for me.

By the way, my CPU is Turion 64 X2 1.6 GHz, and I am running 32-bit version of Edgy.

---

