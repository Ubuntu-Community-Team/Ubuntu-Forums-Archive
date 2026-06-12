---
title: "plasma widgets"
date: 2009-05-09
forum: Desktop Environments
---

### Post by southpawz505 on 2009-05-09
Hello,

I'm fairly new to Ubuntu...been using it a few days and really like it. Recently, I've been trying to add a few widgets to my desktop...in particular the "plasma-widget" set of widgets. I found a few packages I liked (cpuload, memload, clock, stockquote) and wanted on my desktop, so I downloaded/installed them via the terminal by entering

```
sudo apt-get install plasma-widget-cpuload
```This is all well and dandy, but now I can't figure out how to actually get the damn thing on my desktop! I do not see it in my Applications menu.

Any help would be greatly appreciated. Thanks so much in advance.

-Ryan

---

### Post by pjones0404 on 2009-05-09
i typically use screenlets to manage the widgets that i have used. I am not exactly sure what you are trying to install, but you may want to install screenlets. i use gnome but it looks like yo may be using KDE?

if gnome then 

audo apt-get install screenlets. 

Once you have done this you should have a menu item under accessories or you can start it manually from the terminal. Then see if you can install it using the gui there.

---

### Post by southpawz505 on 2009-05-09
Hmm...I would assume that I am using the Gnome Desktop Environment? I am really quite new to all this so I don't quite get how it all works...but in my System menu I have about Gnome...so I would assume that is it.

If you don't mind, would you mind explaining to me, or pointing me the right way to understaning what Gnome/KDE is better?

Also, thanks for the advice on screenlets. This looks to be exactly what I wanted!

---

### Post by andy16666 on 2009-11-12
Gnome is more stable and generally better supported. KDE is not nearly as stable as Gnome, but is far more feature-rich and looks much nicer. It has desktop effects coming out the ying-yang, and better widgets. 

If you find a way to get KDE widgets to work on Gnome, let me know because I really prefer Gnome for its stability and KDE for its widgets.

---

### Post by Amix on 2009-11-13
I think for **GNOME** the best is **gDesklets**, not Plasma widgets,

---

### Post by hidinginthemountains on 2009-12-09
> **Amix said:**
> I think for **GNOME** the best is **gDesklets**...

**Screenlets** is better. gDesklets has pretty spotty maintenence, and lacks the "widget" layer functionality.

---

### Post by iN00B on 2009-12-19
Just install the kubuntu-desktop package from synaptic. Then go into a terminal and type this code 

```
sudo plasma
```

---

### Post by Zorael on 2009-12-19
> **iN00B said:**
> Just install the kubuntu-desktop package from synaptic. Then go into a terminal and type this code 

```
sudo plasma
```
You don't want to run plasma as root, or else you'll end up with all sorts of weird permissions issues.

I believe the plasma desktop package is **plasma-desktop** (plasma netbook being **plasma-netbook**), and it should pull the necessary dependencies. Then just start the binary as your own user, from a terminal or a launcher.
```
$ plasma-desktop
```

---

### Post by afrodeity on 2010-11-15
seems like a waste of resources, just need some of those plasma widgets, not the whole desktop., back here again, still looking for better option.

---

