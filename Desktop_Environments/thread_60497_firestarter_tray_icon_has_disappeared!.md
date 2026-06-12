---
title: "firestarter tray icon has disappeared!"
date: 2005-08-28
forum: Desktop Environments
---

### Post by rah on 2005-08-28
Hi everyone.  I'm new to Ubuntu -- installed it yesterday -- and fairly new to GNU/Linux.  So please bear with me and my noobish questions.

Anyway, I installed Firestarter, and in the preferences I chose to enable the tray icon and to minimize to the tray icon when I close the window.

Then, I was poking around Gnome's top panel, and I accidentally deleted it.  I figured out how to create it again, I put in my clock and volume control and so on, but the Firestarter icon won't come back!

What can I do to fix this?  The program is still working in the background, but I liked the tray icon.... :???:

---

### Post by bLaCk MamBa on 2005-08-28
Oh Crap!!!!!

---

### Post by cwaldbieser on 2005-08-28
[QUOTE=rah]Hi everyone.  I'm new to Ubuntu -- installed it yesterday -- and fairly new to GNU/Linux.  So please bear with me and my noobish questions.

Anyway, I installed Firestarter, and in the preferences I chose to enable the tray icon and to minimize to the tray icon when I close the window.

Then, I was poking around Gnome's top panel, and I accidentally deleted it.  I figured out how to create it again, I put in my clock and volume control and so on, but the Firestarter icon won't come back!

What can I do to fix this?  The program is still working in the background, but I liked the tray icon.... :???:[/QUOTE]
Try opening a terminal and type:
```

$ killall firestarter
$ firestarter

``` 
The first command is in case the GUI process got hung even though the window closed.  The second should restart the GUI.  The actual firewall does not depend on a user process-- it is part of the operating system, so you don't have to worry that you will accidently kill it.

---

### Post by rah on 2005-08-28
Thanks for your suggestion; unfortunately, it simply says that "Operation not permitted" and "no process killed".

---

### Post by wwwDotcoM on 2005-08-28
[QUOTE=rah]Thanks for your suggestion; unfortunately, it simply says that "Operation not permitted" and "no process killed".[/QUOTE]

try sudo killall

---

### Post by tvelocity on 2005-08-28
Maybe you forgot to add the notification area to the panel?

---

### Post by rah on 2005-08-28
That's it!  I didn't realize there was such a thing as a "notification" area.

Thanks very much for your help!

---

### Post by earther on 2008-04-12
OMG!  Thank you for this.  I also deleted what I thought was a separator but it must have been the notification area containing the Firestarter icon.   I've been puzzling and aggravated over this all day.  Now I can relax.  :)

---

