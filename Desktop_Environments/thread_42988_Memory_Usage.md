---
title: "Memory Usage"
date: 2005-06-20
forum: Desktop Environments
---

### Post by wadesmart on 2005-06-20
06202005 0821 GMT-5

Im not completely sure this is a Desktop Support question, and if its not please direct me to the correct location, but, Im looking at the System Monitor and Im seeing some strange things. The clock-applet, Status sleeping, has a VM size of 42.6mb. What the heck is a clock using 46mb of space for?  This evolution-alarm-notify uses 61.8mb..... Im just noticing that my computer is running slower and slower. 

Can I turn some of this off? How would I go about doing that? 

Wade

---

### Post by coolclassic on 2005-06-20
You may find that you are reading the size wrongly try 42.6kb and
61.8kb this would be more realistic.

---

### Post by doclivingston on 2005-06-21
The "memory" column includes all the shared libraries that are loaded for that application. I've put a bit of detail below - but the simple answer is to look at the "RSS memory" column to figure out how muchmemory a program is using.



*More detailed explanation*

Gnome programs all use various shared libraries, such as GTK, Pango, etc. The numbers in the "memory" column include the size of all these shared libraries. The libraries only take up the memory once, but are included in the memory size of every application that uses them.

The "RSS memory" column is the amount of memory that has been allocated to the application's heap - which is fairly close to "how much memory is this program using?".

---

### Post by WMCoolmon on 2005-07-08
Is there a way to tell how much memory will be freed if you get rid of an app or close a program?

---

### Post by alastair on 2005-07-08
Using "ps axl" will show memory :

VSZ - virtual memory used
RSS - actual memory used (resident)

My "clock applet" (/usr/lib/gnome-panel/clock-applet) uses :

18012 MB virtual
8624 MB resident

As stated previously though, much of this is "shared" via shared objects/libraries.

---

### Post by doclivingston on 2005-07-09
[QUOTE=WMCoolmon]Is there a way to tell how much memory will be freed if you get rid of an app or close a program?[/QUOTE]

Not really - it will depend on whether other programs are using the same shared libraries. I'm not aware of a tool that will tell you exactly what will be unloaded, and how much memory it will free.

Some of the core libraries used by the desktop are never going to get unloaded (GTK, etc); some shared libraries only get used by one program (particularly some of the Evolution libraries).

---

