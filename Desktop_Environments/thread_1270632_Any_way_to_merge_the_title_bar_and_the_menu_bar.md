---
title: "Any way to merge the title bar and the menu bar?"
date: 2009-09-19
forum: Desktop Environments
---

### Post by gamelord12 on 2009-09-19
[http://www.gnome-look.org/content/show.php/Combined+titlebar%2Bmenubar+-+MOCKUP?content=89412](http://www.gnome-look.org/content/show.php/Combined+titlebar%2Bmenubar+-+MOCKUP?content=89412)

The link above is an example of exactly what I want.  Songbird does this even in its Windows version, and it's a great way to maximize window space (like IE7, IE8, and Windows Vista's Explorer do, but without the annoyance of having to hit the Alt key to access your menu bar).  Is there any program that allows you to tweak the way GNOME draws your windows so that this can be done?

---

### Post by mexlinux on 2009-09-20
I want that too

---

### Post by gamelord12 on 2009-09-21
Does this functionality exist in any form?  I have a vague enough understanding of how GNOME places different parts of windows on the screen, but I don't really have the time to add another project to my list of things I want to program, or else I'd write it myself.

---

### Post by mcduck on 2009-09-21
No, it's not possible. the window manager handles window frames and titlebars, and is completely separate from the programs running inside the windows and the toolkits used to draw application interfaces.

Implementing such thing in reality would require writing a completely new window manager and  similar hacks to GTK that are currently used to move the application menu into a panel widget to get the mac-style unified toolbars.

edit: Of course if you also want to keep the desktop effects things get even more complicated since they are provided by Compiz, which is a window manager and you can't run two at the same time..

---

### Post by VCoolio on 2009-09-21
mcduck is right, but you can get both window title and buttons and the menu on the gnomepanel. For title bar check [Namebar]("http://www.gnome-look.org/content/show.php/NameBar?content=101643"), for menu check [global menu applet]("https://wiki.ubuntu.com/global_menu").

---

### Post by gamelord12 on 2009-09-22
So then how does Songbird do it?  If it overrides the window manager, couldn't you just write a plugin for Compiz that would work for every program?

---

### Post by mcduck on 2009-09-25
> **gamelord12 said:**
> So then how does Songbird do it?  If it overrides the window manager, couldn't you just write a plugin for Compiz that would work for every program?

You'd have to write that in every program themselves, not in Compiz.

If the program overrides the window manager there's little the window manager can do to alter the program's looks.

---

### Post by londonali1010 on 2009-09-25
I'm pretty sure you can something like it in Openbox by setting your rc.xml to not draw window decorations on certain windows. Then you'd just have the menu bar and have to use something else (keybindings/mousebindings) to minimise, maximise etc. But Openbox does that pretty easily, so it might be an option, but only if you want to switch DEs!

---

### Post by mcduck on 2009-09-25
> **londonali1010 said:**
> I'm pretty sure you can something like it in Openbox by setting your rc.xml to not draw window decorations on certain windows. Then you'd just have the menu bar and have to use something else (keybindings/mousebindings) to minimise, maximise etc. But Openbox does that pretty easily, so it might be an option, but only if you want to switch DEs!

Any window manager can do undecorated windows. That's not a problem. Most will do that if a program asks the WM to not decorate it, but usually there's also a way to define undecorated apps manually. For example in Compiz you can simply add your programs/window types in the Window Decoration-plugin's settings.

Undecorating a window is easy. Moving part of the window's contents somewhere else than inside that window, like into the decorations, is hard.

---

