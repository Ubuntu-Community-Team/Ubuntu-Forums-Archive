---
title: "Cursor Launch Feedback?"
date: 2005-04-12
forum: Desktop Environments
---

### Post by Deusiah on 2005-04-12
Is it true that Gnome has no support for this most obvious of OS functions? A search on Google reveals no answers but a bit of history as can be seen below:
[http://www.linuxselfhelp.com/gnome/users-guide/alf.html](http://www.linuxselfhelp.com/gnome/users-guide/alf.html)

Gnome did once have Launch Feedback so it's either droped it or I can't find it :-k

Any feedback on this would be much appreciated thanks ;)

---

### Post by alexp on 2005-04-12
Deusiah,

AFAIK, this (at least in the shape of a special mouse cursor) doesn't exist anymore. However, when clicking on a launcher, the window list almost immediately gets a new entry saying "Starting <appname>...".

Regards,
Alexander

---

### Post by mendicant on 2005-04-12
When I launch an application from a menu, and the app is loading, the cursor changes to a circle with hash marks in it, and it is animated so it looks kind of like a hand on a clock, spinning.  Hard to describe, and I can't take a screenshot of it, but it does indicate that it is busy.  This only seems to happen with some apps--not Tuxpaint, for instance.

---

### Post by Deusiah on 2005-04-12
Yes my apologies it does indeed work with some apps just not all of them :neutral:

---

### Post by reedlaw on 2005-08-18
How can we get startup notification for such programs as firefox and openoffice?  Are there any hacks out there to make this work?  (I haven't found any on google yet)

---

### Post by reedlaw on 2005-08-18
I just found out how to do this in OpenOffice and some other programs:
Add the following line in the .desktop file for the application launcher:
StartupNotify=true

However, this doesn't work in Firefox.  The cursor changes to the spining wheel but an extra task is kept running in the panel even after Firefox is closed.  Any suggestions on how to fix this?

---

