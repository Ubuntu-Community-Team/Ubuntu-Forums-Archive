---
title: "put amarok tray icon back (gnome)"
date: 2007-01-24
forum: Desktop Environments
---

### Post by eldersoares on 2007-01-24
well, i have accidentally quited the amarok tray icon from the panel in gnome and now i want to put it back!!!!!!! how can i do that?!?!?!??!?!?!?!

---

### Post by usererror on 2007-01-24
I don't know.  I have a problem with mine not showing up in the tray but in a floating tray that I can drag all around the desktop.  :confused:

---

### Post by nalmeth on 2007-01-24
This is caused by problems communicating by klauncher.
It is solved by running:
```
kdeinit
```
In the terminal of your choice

---

### Post by eldersoares on 2007-01-24
actually, it doesnt happen only w/ amarok. it seems that its w/ all applications that put a tray icon 'cause the gaim icon also doesnt appears! i clicked w/ the right bottom and accidentally put "quitar del panel" (in spanish) that must be, in eng, quit from the panel. and if i put add to the panel, there are some options but not the ones i want...

---

### Post by JALenon on 2007-02-18
I had the same problem.

Right click on you top panel.

Select "Add to Panel..."

Select "Notification Area" - this was one of the last listed for me.

A Notification Area - including your Amarok icon - should appear on the top panel.

Move it where ever you wish.

---

### Post by Korsaire71100 on 2007-03-04
Thank you very much, it solved this really stupid "problem" for me.


> **JALenon said:**
> I had the same problem.

Right click on you top panel.

Select "Add to Panel..."

Select "Notification Area" - this was one of the last listed for me.

A Notification Area - including your Amarok icon - should appear on the top panel.

Move it where ever you wish.

---

### Post by brodiepearce on 2007-03-07
I just installed Amarok (using Dapper), and now my program icons no longer appear in the workspace squares in the bottom right corner...

Anyone got any ideas why this has happened/how to fix?

*edit*
After restarting the problem doesn't seem to exist anymore, as they say, it is a mystery. :P

---

### Post by mlissner on 2007-08-12
> **nalmeth said:**
> This is caused by problems communicating by klauncher.
It is solved by running:
```
kdeinit
```
In the terminal of your choice

Worked like a charm. Thanks. I will add that you need to close amarok before this will work, and I have a feeling that running:
```
kdeinit > /dev/null 2>&1
```would have been wise to pipe out the error message.

---

