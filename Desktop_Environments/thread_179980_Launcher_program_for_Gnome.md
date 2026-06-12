---
title: "Launcher program for Gnome"
date: 2006-05-21
forum: Desktop Environments
---

### Post by Hanj on 2006-05-21
There seems to be hundreds of clones of the MacOS X launcher bar out there, but wouldn't it be more convenient to have the launcher pop up right under your mouse? What I'm looking for is some kind of program that lets me press some keyboard shortcut and then shows a menu with commonly used programs (customizable of course). Anyone know if such a program exists for Gnome? Or do I have to code it myself?

---

### Post by art on 2006-05-21
Have you seen deskbar-applet? Or katapult for KDE, but you can use it even with gnome. Is that what you are looking for?

---

### Post by Hanj on 2006-05-21
Deskbar is really nice, but it still requires me to type the name of the application to start (unless I've missed some feature?). What I want is basically something like [this]("http://www.kde-look.org/content/show.php?content=34681"), only it should stay hidden until I press some keyboard shortcut, and then appear under the mouse pointer. It doesn't have to be that advanced, just a menu with my favorite applications. Having a lot of icons in a panel takes up a lot of screen space, and having to type the name of an application or looking it up in the gnome menu seems really inefficient.

I haven't looked at katapult, but from what I see, it looks very similar to deskbar.

---

### Post by art on 2006-05-21
Well, I think I understand what you are looking for. Deskbar if you have the latest version at least, if you click on it gives you the latest programs used. There is a gdesklet called CircleButtonBar, which looks like the thing from the link, but is not entirely the same... Katapult is indeed similar to deskbar, or OSX's QuickSilver. On the other hand you can always configure shortcuts to launch any application you want, with xkeybindings.

---

### Post by Hanj on 2006-05-21
> Deskbar if you have the latest version at least, if you click on it gives you the latest programs used.Maybe I should take a closer look at deskbar...

Anyway, this might be a good coding project for the summer, I'll post here if I should make something useful.

---

### Post by Nonno Bassotto on 2006-05-21
gDesklets are configured to show up when you press some button (default Shift+F12). So I think a gDesklet like this
[http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=127](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=127)
or this
[http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210)
could do the trick. Actually they don't appear under your mouse, and the graphic effect is not very nice, because of transparence. If you use a composite manager, then the desklets work with transparence and the visual effect will be much better.

---

### Post by Hanj on 2006-05-22
Thanks for the tip! It looks really bad when using Xgl though...

---

### Post by Nonno Bassotto on 2006-05-22
Did you enable the option to let gDesklet use the composite manager? It's under gDesklets configuration. Hope it works.

---

### Post by Hanj on 2006-05-22
I still can't make it work correctly. Transparency doesn't work and it seems to slow down Xgl. Guess that's what you get from playing around with software that's not finished though...

---

