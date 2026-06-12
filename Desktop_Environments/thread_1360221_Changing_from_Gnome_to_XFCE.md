---
title: "Changing from Gnome to XFCE"
date: 2009-12-20
forum: Desktop Environments
---

### Post by humphreybc on 2009-12-20
Hi,

So I installed Ubuntu on this crappy old Pentium computer that we've got to use as a Guest computer. While everything is set up and works nicely, it's soooo sluggish. I installed Ubuntu/Gnome because that's what I'm most familiar with, but if XFCE will improve the speed then it's worth the tradeoff of being unfamiliar with XFCE.

So I've never actually switched desktop managers before on an installed system, I presume all you need to do is:

```

sudo aptitude install xubuntu-desktop

```

And let aptitude sort out the rest? Space is limited, so I don't want to keep Gnome and choose either at login - I just want XFCE.

This will work, right?

---

### Post by snowpine on 2009-12-20
Yes, it will work...and here's how to remove Gnome:

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by gradinaruvasile on 2009-12-20
Yes, it should work like that. but i would advise a full reinstall if you want to see Xfce at full speed. There are many Gnome components that may load at startup if installed slowing the computer.

I use Xfce on a Dell D630 (2.0 GHz Core2Duo CPU) thats fairly new hardware - but it is noticeably faster (and more responsive) than Gnome was. 

Xfce is really nice, but some stuff work differently/are not included like in Gnome. Some examples:
- Mounting shares needs gigolo (this is the application name), Thunar (xfce's nautilus equivalent) doesnt integrate share like Nautilus. And you should install the gnome-mount package for gigolo really to work (mount shares). I added Gigolo to autostart - i have its icon permanently in the tray, i just click on it if i want to mount a samba/ssh share. 
- There is no working menu editor, or maybe there is one that doesnt work yet. This is somewhat balanced out by the fact that you can create menus - the taskbar launchers are, in fact menus, you can add/remove items easily.
I read somewhere that a working menu editor is in the works.
- Some apps installed from the repositories will not have their icons in the menus - this is because the menu structure differs from Gnome's that is the basis for Gtk apps.
- It uses much less RAM than Gnome - there isnt that much stuff loaded in the memory on startup.
- No Compiz preinstalled. The idea is to keep the desktop fast.
- You can install any Gtk application you want, Xfce (at least the Ubuntu version of it) is based on Gtk like Gnome. In fact Xubuntu is Gnome-Lite in essence. But check what you are installing because if you install Gnome core apps like nautilus/evolution it will bring tons of (Gnome) dependencies and you will end up with Gnome(sort of) in the end again. I avoid  installing Gnome core applications - that would negate the whole idea of installing Xfce.

---

### Post by snowpine on 2009-12-20
> **gradinaruvasile said:**
> Yes, it should work like that. but i would advise a full reinstall if you want to see Xfce at full speed. There are many Gnome components that may load at startup if installed slowing the computer.

Nope, just follow the easy tutorial I linked to above to remove the Gnome stuff... no need to reinstall.

---

