---
title: "Evolution fails"
date: 2005-11-27
forum: Desktop Environments
---

### Post by Orval on 2005-11-27
All of a sudden Evolution fails to start.

Starting in konsole gives the following messages:

```

(evolution-2.4:9857): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed
QPixmap: Invalid pixmap parameters
QPainter::begin: Cannot paint null pixmap
QPainter::setPen: Will be reset by begin()
QPainter::setBrush: Will be reset by begin()
QPainter::setBrush: Will be reset by begin()
QPainter::setPen: Will be reset by begin()

```

What can I do to restore Evolution. I already tried to reinstall Evolution, but that didn't have the desired result.

---

### Post by Orval on 2005-11-28
By the way: evolution starts OK when I start it from Gnome. However, I like KDE better... Other Gnome-applications work in KDE for as far I tried them.

---

### Post by Orval on 2005-11-28
Great. Now Evolution fails under Gnome too.

Please help.

---

### Post by Orval on 2005-11-29
Finally I solved the problem. I removed the gdk-gc packages and now everything works fine again.

---

### Post by royg1234 on 2005-12-11
[QUOTE=Orval]Finally I solved the problem. I removed the gdk-gc packages and now everything works fine again.[/QUOTE]

I don't see this package in Synaptic (apt-get can't find "gdk-gc" either).  Can you give me a list of the packages you removed?

I can open mail, but it breaks when I go into the calendar.  Here's the terminal output

```

(evolution-2.2:20446): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.
adding hook target 'source'
Setting up initial mail tree
addressbook_migrate (0.0.0)

(evolution-2.2:20446): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS _GC (gc)' failed

(evolution-2.2:20446): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS _GC (gc)' failed

(evolution-2.2:20446): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS _GC (gc)' failed


```

---

### Post by royg1234 on 2005-12-11
it seems that the calendar is the only part of evolution that breaks.  And it breaks only when I switch to a Clearlooks-Cairo theme.

---

