---
title: "metacity,nautilus and ??"
date: 2008-06-22
forum: Desktop Environments
---

### Post by dexter.deepak on 2008-06-22
i just tried to "see" the difference between nautilus and metacity (i had only read bout them)
i logged in a failsafe terminal and launched nautilus first.it gave me the file manager,desktop icons,etc...and i could open all the gui applications..all without the title bar and the minimize/maximize/close buttons.
on launching the metacity, i could now get the title bar and the buttons.

in both the cases, my menu bar, i.e the desktop panel, the window switcher,desktop switcher were absent.
<alt>+<tab> keys worked ..but only when i was running metacity and didnt run when i was running nautilus alone.

so it would be kind if someone explains me :
1. the "panel" is a component of what component of Xwindows ? what do i need to invoke, if i want it running ?
2. (once more) the difference b/w nautilus and metacity/

thanks a lot...

---

### Post by vishzilla on 2008-06-22
1. Panel can act as a launcher or taskbar. You are read further here [[link]("http://en.wikipedia.org/wiki/Gnome-panel")]


2. Nautilus is the file manager equivalent to Windows Explorer in Windows. Metacity is the Window manager that deals with the behavior of a Window like maximize, minimize, close, resize, move.

---

### Post by dexter.deepak on 2008-06-22
thanks for the second explanation, but the first point i cant understand.
 
what i thought was that metacity and nautilus could take care of everything on the desktop...but was shocked to see that panel couldnt be launched through these two alone.
thats why i was asking whats the third component that takes care of the panel....
but i got the answer now...the panel is itself an application, which is invoked by command "gnome-panel"

nyways...thanks !!

---

### Post by atomkarinca on 2008-06-22
To get things a little clearer, Metacity is a [window manager]("http://en.wikipedia.org/wiki/Window_manager") where nautilus is a [file manager]("http://en.wikipedia.org/wiki/File_manager"). When you run Gnome (which is a [desktop environment]("http://en.wikipedia.org/wiki/Desktop_environment")), it runs the WM, FM, panels and a couple of daemons and tools.

---

