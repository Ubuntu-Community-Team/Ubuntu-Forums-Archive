---
title: "I still haven't found the right DE/WM"
date: 2007-12-26
forum: Desktop Environments
---

### Post by blithen on 2007-12-26
I want one that has the customization of KDE, but has menus somewhat like GNOME.
In KDE:Keyboard shortcuts for everything and the deep customization.
In GNOME: The ease of doing all of that. And the menu types.
In my opinion it's kind of a pain to setup up everything in KDE
So is there a DE/WM that can do that?

---

### Post by samwyse on 2007-12-26
I hope KDE4 will make the developers sort out all the menus and dialogs.

---

### Post by Onyros on 2007-12-26
> **blithen said:**
> I want one that has the customization of KDE, but has menus somewhat like GNOME.
In KDE:Keyboard shortcuts for everything and the deep customization.
In GNOME: The ease of doing all of that. And the menu types.
In my opinion it's kind of a pain to setup up everything in KDE
So is there a DE/WM that can do that?Even though I already stopped using it altogether, I don't think GNOME is as hard to customize as most people deem it to be.

KDE is an utter mess, for me; GNOME's configuration options are usually hidden somewhere, but most of them are accessible through a good skimming of options with gconf-editor. Sometimes things will need a further step to configure, but there really isn't anything in GNOME I couldn't configure that I could in KDE.

I prefer GNOME's approach: a few basic customization options are easily accessible. If you want some power-user tweaking you'll have to get your hands a little more dirty. Makes for less cluttered option menus and even user menus. I also prefer to do some of the tweaking in config files directly, so it goes with my preference.

And just to clear this up, I'm not going into any WM/DE wars. I got fed up of GNOME myself. I'm just stating what is my view and personal preference. :)

---

### Post by K.Mandla on 2007-12-26
Moved to Desktop Environments.

---

### Post by blithen on 2007-12-26
> **samwyse said:**
> I hope KDE4 will make the developers sort out all the menus and dialogs.

Holy crap yes. It just seems so cluttered and hard to do.

---

### Post by BLTicklemonster on 2007-12-26
I like IceWM. Though you really have to go messing around and typing stuff, you can get it to look like darned near anything you want it to.

This thread, albeit a marathon of sorts, has some great tips:

[http://ubuntuforums.org/showthread.php?t=263710](http://ubuntuforums.org/showthread.php?t=263710)

I"m playing around in XFCE right now, and it's come a long way, too.

---

### Post by jseiser on 2007-12-26
key bindings can be set up very easily using xbindkeys, its probably in the repos or you can install from source.  You just put like
"firefox"
Alt + b
and hitting alt b will launch firefox, the config is well documented.  
So if that was a major flaw, then really, all of the good window managers would work very well, evilwm, openbox, xmonad, rat poison.  Customizing with the window managers is normally as easy as.  put icon theme in ~/.icons, edit gtk2rc.mine and add the name, themes for gtk2/1 in ~/.themes, and use gtk-chtheme to load the new themes.  Menus in opebox are easy with obmenu, or menumaker.  I know you can grab both from source easy.  Another good bet is to install a gmrun or something like it, to launch less used apps.

---

### Post by urukrama on 2007-12-27
I love Openbox, and IceWM. I suggest you install a few window managers and/or desktop environments and see what you like best. Screenshots don't always tell you what you can do with a DE or WM. (KDE can have extra menus, for example).

---

