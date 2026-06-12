---
title: "Running Gnome in Cygwin."
date: 2009-04-08
forum: Desktop Environments
---

### Post by jwbrase on 2009-04-08
I just installed Cygwin on the Windows side of my machine, and Gnome along with it through the Cygwin setup program, but I'm not entirely sure how to get X to load Gnome, having not really done any messing with configuring X in Ubuntu. Any pointers?

---

### Post by kreggz on 2009-04-08
Try this URL:

[http://cygnome.sourceforge.net/run.html](http://cygnome.sourceforge.net/run.html)

---

### Post by jwbrase on 2009-04-08
Looks like instructions for an older version of Cygwin and/or Gnome. The path /opt/bin/gnome/* is mentioned alot, and /opt does not exist on my copy of Cygwin. (Gnome is in there, but I'm not sure which path I need to substitute into the instructions for /opt/bin/gnome/*, and what other changes I might need to make).

---

### Post by sleepyjon on 2009-04-08
Try using:

```

find / -name gnome

```

in cygwin.

---

### Post by driftingprogrammer on 2011-11-30
on cygwin 1.7 there does not seem to be any gnome-session executable. Has anybody been able to start gnome on the latest cygwin 1.7?

---

