---
title: "Widget spy application :]"
date: 2006-03-06
forum: Desktop Environments
---

### Post by Kray on 2006-03-06
Microsoft Visual Studio contains (or used to contain, not sure about recent versions) small handy app (unfortunately I don't remember name :/), which gives info about windows controls (widgets) like Button, ComboBox, ListView etc. After launching this app one could click any control on screen and get detailed info about in (type, class, parent hierarchy...).

I wonder if similar app exists for Gnome (GTK)?

Why I need such app? I'm curently fighting with theming my gnome-panel. The biggest issue is notification area - some apps (icons) have corrent background now (Gaim), other (Rhytmbox, gDesklets...) are drawn on white background (I'm pretty sure that these icons are transparent). If I got widget class name and/or widget hierarchy I think I should be able to add correct styles in my gtkrc file.

*Edit:*
Ok, I found this app from Visual Studio. It is called Spy++, u can see example screenshots here: [http://support.citrix.com/article/CTX103137]("http://support.citrix.com/article/CTX103137").

Now, give me same for GTK ;-)

Kray

---

### Post by tobiasz.cudnik on 2008-04-03
Looking for same thing.

---

### Post by Halcyone1024 on 2008-04-05
Back when I was using Kubuntu Dapper, I was fiddling around with window-specific settings, and I found something that reported the class names of individual windows and dialogs.  All you did was hit the button and click on another window, and it would bring up the class name (of the window, not the controls), and maybe a couple other things as well.  I'm assuming that that by itself won't help you, but whatever program or SO that KDE's System Settings uses to provide this functionality might be capable of more than it's used for.  After all, why bother with introspection at the control level when your problem is at the window/dialog level?

I couldn't find any new processes popping up when I tried it in KDE4 just now, so it's probably an SO.  Does this ring a bell for anyone, or does anyone know how to tell which SO's an application is using?  I'm sure that if one exists, someone's coded a front end to it that'll do what you want.  Of course, there are many more different ways of implementing controls on Linux than there are on Windows, especially when we're talking about Visual Studio, so such a hypothetical program might run into roadblocks once in a while.

---

