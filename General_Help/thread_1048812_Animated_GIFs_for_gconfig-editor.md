---
title: "Animated GIFs for gconfig-editor?"
date: 2009-01-23
forum: General Help
---

### Post by brsmits on 2009-01-23
I am all happy with some of the buttons and options and icons that I am creating with Gnome Configuration Editor, but it does not support animated gifs.  Does anyone know how I could change this fact?

(I just think that a menu button that is a dude running around would be kinda funny)

---

### Post by mcduck on 2009-01-24
Download the source code for the program you wish to be able to use animated icons and edit the program to add support for them.. For example if you want the Gnome's menu applet to use animated gif as icon you'll need to reprogram the menu applet to support that.

Sorry, there really is no other way.

(In other words your problem is not gconf-editor, it's just hat the programs which setings youa re trying to change simply don't support animated icons. There's nothing gconf-editor can do about that. It only changes lines of text in some XML configuration files.)

---

### Post by brsmits on 2009-01-26
I don't have enough experience to even BEGIN a project like that.  But it's an idea!  I think it would be cool, anyone else?

---

### Post by brsmits on 2009-06-04
Strangely enough, I solved the problem without even looking for it at the time.  Apparently there is a fish you can add to a Panel.  The fish is an animated icon that will also run a command on a click.  Sounds exactly like what I was going for!  WOO!!  Time for excessive bells and whistles to clutter the crap out of my panels now!!!

---

