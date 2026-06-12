---
title: "Make windows remember their position and size?"
date: 2012-04-08
forum: Desktop Environments
---

### Post by santosh83 on 2012-04-08
Hello all,

Is there a switch somewhere I can toggle to make all application windows remember their last active position and size, for the GNOME (2.x) desktop environment, using compiz (though I'd readily change to metacity if it supports this) as window manager?

There doesn't appear to be any obvious control anywhere. I investigated the 'Fixed Window Placement' tab of 'Place Windows' module in ccsm, but it is only for manually specified windows, while I want **all** windows to remember their previous position and size. In addition, even for specific applications, I was not able to figure out how exactly to add an application to the 'Windows with fixed position' field in 'Place Windows.'

The 'Put Windows' module annoyingly doesn't work properly for me here. I enabled a shortcut key for 'Restore Position' function, but when I activate it, the window is placed quite a bit away from the actual previous position. Sometimes the titlebar goes "behind" the panel, forcing me to 'ALT grab' the window to move it back.

So is there *any* way at all to make GNOME remember my window positions at least, if not size? Or does anyone know of any other DE (KDE? Xfce?) or window manager that has this functionality? It'd be **very** useful for me!

Thanks.

---

### Post by Ravi5kumar on 2012-04-08
> So is there *any* way at all to make GNOME remember my window  positions at least, if not size? Or does anyone know of any other DE  (KDE? Xfce?) or window manager that has this functionality? It'd be **very** useful for me!I think it is a bug. Not a bug in Gnome 2 but in applications.If  a app  remembers its last opened position then it is  fine. But if not then  Gnome puts in top left side of the screen. As far as I know no DE is available or window manager has that functionality. Read here about this bug [https://bugzilla.gnome.org/show_bug.cgi?id=162643](https://bugzilla.gnome.org/show_bug.cgi?id=162643)

---

### Post by santosh83 on 2012-04-08
> **Ravi5kumar said:**
> I think it is a bug. Not a bug in Gnome 2 but in applications.If  a app  remembers its last opened position then it is  fine. But if not then  Gnome puts in top left side of the screen. As far as I know no DE is available or window manager has that functionality. Read here about this bug [https://bugzilla.gnome.org/show_bug.cgi?id=162643](https://bugzilla.gnome.org/show_bug.cgi?id=162643)

Oh! That's disappointing. If Ubuntu should find success with Average Joe users then these type of minor annoyances need to ironed out. Placing windows manually by dragging *every* single time the app is opened is quite irritating!

Nautilus alone seems to remember it's last placed position though.

I don't agree it's entirely an app's responsibility to remember its previous position. IMO, the window manager also has to record this, and if an app doesn't request placement at a certain position, then the WM should place it according to user's settings, which is what it does do currently, **but** with the glaring exception of having an option to tell it to place at the previous position!

Thanks anyway.

---

### Post by Ravi5kumar on 2012-04-08
Hope they will fix it soon so users like you and me not get annoyed by always dragging windows form top left corner.....

---

### Post by RobinSchouten on 2012-05-25
I am still wishing for someone to finally fix this! It has been bugging me for years now!

---

### Post by Ravi5kumar on 2012-05-25
The ubuntu developers should create a software which runs in background and record every application size and position and restore it when user again starts that application. I am on kubuntu 12.04 and still this issue is not fixed. When they will fix it.......?

---

