---
title: "Adobe AIR files won't install properly."
date: 2009-05-03
forum: General Help
---

### Post by jherievans on 2009-05-03
I have properly installed Adobe AIR, but anytime I try to access a .air file a small AIR Application Install window pops up for a moment and then goes away and nothing further happen. I have tried uninstalling AIR and then reinstalling it and have still had no luck. Can anyone help me?

Also, I am using 8.10, with all updates.

---

### Post by SanJuan on 2009-05-03
I have the same problem, under Ubuntu 9.04 32 Bit, I've tried everything the past 2 days, and kinda getting to the point where I say to tijuana with it, and going back to Windows...

---

### Post by jherievans on 2009-05-04
Anyone know what's going on, or have any ideas?

---

### Post by jherievans on 2009-05-09
One more feeble attempt for help...

---

### Post by binbash on 2009-05-09
a terminal output will be fine.Until seeing any outputs, all i can say that i used adobe air on both intrepid and jaunty and it works fine here.

---

### Post by SanJuan on 2009-05-09
I've tried to install thru Terminal, I've tried almost everything.

It won't work.

You said Terminal Output. Tell me how to make one, And I'll give it to you.

---

### Post by SanJuan on 2009-05-09
Terminal Says

Application crashed with an unhandled SIGSEGV
Segmentationfault

---

### Post by swatsbiz on 2009-05-11
Bump:

Here's my output:

> Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgiofam.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiofam.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
Application crashed with an unhandled SIGSEGV
Crashlog has been dumped in /tmp/airCrashLogs/0511_1124_9zLQjd


And the crashlog:

---

### Post by SanJuan on 2009-05-11
Tell me how to make such an output and I'll make it.

---

### Post by swatsbiz on 2009-05-11
> $ cd usr/bin
$ Adobe\ AIR\ Application\ Installer 


That should do it

---

### Post by SanJuan on 2009-05-12
How do I make the error log?

---

### Post by swatsbiz on 2009-05-14
It tells you at the end where it has placed the error log, probably in usr/temp

---

### Post by swatsbiz on 2009-05-14
I think this is a 64bit compatibility issue, I have found this site:

[Link]("http://www.adoleo.com/blog/2009/apr/5/installing-adobe-air-ubuntu-jaunty-64-bit/")

but I'm stuck on changing the GTK_PATH part, if someone could point out what to do it would be appreciated

---

### Post by SanJuan on 2009-05-21
Attached is my error log.

Help please.

---

### Post by swatsbiz on 2009-05-22
bump ... anyone with an idea?

---

### Post by SanJuan on 2009-05-22
Bump. Anyone have an idea?

---

