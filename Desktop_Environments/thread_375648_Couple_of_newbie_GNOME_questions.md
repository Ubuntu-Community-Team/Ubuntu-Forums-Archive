---
title: "Couple of newbie GNOME questions"
date: 2007-03-04
forum: Desktop Environments
---

### Post by FooSoft on 2007-03-04
I'm fairly new to Ubuntu (Edgy 6.10), got everything working and now I'm messing around a little bit with the UI. I've got a couple of things I can't figure out though:

1) How do I prevent current mounts from automatically showing up on the desktop? For example, I have an internal SATA drive mounted all the time; does it really have to take up desktop space?

2) Any way to prevent windows from "snapping" when I move them? (currently they snap to desktop edges, other windows, pretty much anything; I can't move a window without it constantly snapping to something)

3) What would be a good recommendation for an OS X style dock (for launching applications)? 

Thanks guys.

---

### Post by aysiu on 2007-03-04
#1. Press Alt-F2 and type ```
gconf-editor
``` Then go to Apps > Nautilus > Desktop and uncheck the one about showing Volumes on the desktop.

#2. I'm not sure where exactly it is, but I'm sure there's something in *gconf-editor* about window behavior. Maybe in Apps > Metacity

#3. Maybe [Gnome Dock](http://www.gnome-dock.org/trac)?

---

### Post by FooSoft on 2007-03-04
Excellent, thanks. Got the volumes under control. Couldn't figure out how to get rid of window snap yet, but gconf-editor has a lot of stuff I can tinker with. Also while looking at gnome-dock, I found out kiba-dock, which might be worth a try as well :)

---

### Post by Zyphrexi on 2007-03-04
are you by any chance running a composition manager ala beryl/compiz?

---

### Post by FooSoft on 2007-03-04
I'm not running beryl/compiz now, but it looks like it would be fun to try

---

### Post by Zyphrexi on 2007-03-06
I've been kind of playing around with gimmie... while not really being a dock, is pretty cool when added to an existing panel.

---

