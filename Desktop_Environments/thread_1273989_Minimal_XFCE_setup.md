---
title: "Minimal XFCE setup"
date: 2009-09-24
forum: Desktop Environments
---

### Post by jhsu802701 on 2009-09-24
I'm setting up a laptop for the Data Acquisition Prototype subgroup of Project Phoenix, an IEEE study group working on an open-source blood pressure monitor.

The challenges:
1.  The laptop I'm setting up is a 10-year-old Dell with only a 500 MHz processor and 256 MB of RAM.  In fact, it was originally equipped with Windows 98.  The default installations of regular Ubuntu and even Xubuntu are too heavy for this laptop.  Thus, I'm using a minimal install and trying to figure out what packages I need to add.
2.  We need engineering and math software.  Ubuntu has a wide variety of packages in the repository.
3.  The other engineers in the group aren't familiar with Linux, so it's important that I make the setup easy for them to use.  That's why I'm using Xubuntu instead of Debian.  I tried playing around with JWM and Fluxbox, but they're not that well supported in Ubuntu.  (They're fully functional right out-of-the-box in Puppy Linux.  Making them equally functional in X/ubuntu takes too much tinkering.)  Thus, I'm going with XFCE - faster than GNOME but better-supported in Ubuntu than Fluxbox and JWM.
4.  We need the wireless networking to get onto the Internet from our lab.  The wireless card is a Linksys WPC54GS v1.1.

Given all this, after the alternate command-line installation of Xubuntu, what is the MINIMUM (in terms of RAM required) set of packages needed to make XFCE fully functional for us?  I only want to install the software we actually need, but the default Xubuntu installation includes too many memory-hogging applications that we don't need.

---

### Post by kerry_s on 2009-09-24
minimal xfce4:
```
sudo apt-get install xorg gdm xfce4 synaptic
```

you can use synaptic to install what ever else you need.

you can actually tweak gnome to use lower resource then xfce4 or most window managers. i'm using gnome(jaunty) on 450mhz 256mb ram.

minimal gnome:
```
sudo apt-get install xorg gdm gnome-core synaptic
```

try this guide for gnome:
[http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en](http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en)

---

### Post by jhsu802701 on 2009-09-24
> **kerry_s said:**
> minimal xfce4:
```
sudo apt-get install xorg gdm xfce4 synaptic
```you can use synaptic to install what ever else you need.

you can actually tweak gnome to use lower resource then xfce4 or most window managers. i'm using gnome(jaunty) on 450mhz 256mb ram.

minimal gnome:
```
sudo apt-get install xorg gdm gnome-core synaptic
```try this guide for gnome:
[http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en](http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en)


I'll  have try the stripped-down GNOME installation.  I can't believe that barebones GNOME is as light as barebones XFCE, JWM, IceWM, etc.  If barebones GNOME is fast enough, I'm sticking with it, as Ubuntu seems to revolve around GNOME.  I think the Ubuntu development team has mostly GNOME users, and they make sure things work well out-of-the-box in GNOME.  I think very few of the Ubuntu developers use JWM, Fluxbox, IceWM, etc., and that's why so much tinkering is needed to make everything functional.  By contrast, most of the Puppy Linux developers use JWM, Fluxbox, etc. and make the adjustments needed to make sure things work out-of-the-box, and that's why these lightweight window managers work so well out of the box.

---

### Post by kerry_s on 2009-09-24
> **jhsu802701 said:**
> I'll  have try the stripped-down GNOME installation.  I can't believe that barebones GNOME is as light as barebones XFCE, JWM, IceWM, etc.  If barebones GNOME is fast enough, I'm sticking with it, as Ubuntu seems to revolve around GNOME.  I think the Ubuntu development team has mostly GNOME users, and they make sure things work well out-of-the-box in GNOME.  I think very few of the Ubuntu developers use JWM, Fluxbox, IceWM, etc., and that's why so much tinkering is needed to make everything functional.  By contrast, most of the Puppy Linux developers use JWM, Fluxbox, etc. and make the adjustments needed to make sure things work out-of-the-box, and that's why these lightweight window managers work so well out of the box.


that's my thought exactly. i just did a custom lenny gnome install & it's running damn nice, still getting things setup, but it's mostly there.

---

### Post by Bucky Ball on 2009-09-24
Do you need to use Gnome? The instructions given before would probably work if you leave out gdm . Lot less juice that a Gnome DE. 

```

sudo apt-get install xorg xfce4 synaptic
```You could also go the CLI install and just install the bits you need (like synaptic if you need the cute GUI to install things). You might be happy in a terminal using apt-get.

Xfce so much more efficient!

---

### Post by earthpigg on 2009-09-24
have you considered LXDE?

lightweight, but not quite as light as jwm or fluxbox.

and a full desktop environment.

---

