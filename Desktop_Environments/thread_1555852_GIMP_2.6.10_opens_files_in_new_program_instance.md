---
title: "GIMP 2.6.10 opens files in new program instance"
date: 2010-08-18
forum: Desktop Environments
---

### Post by KonfuseKitty on 2010-08-18
I didn't have this problem in GIMP 2.6.8: when I double clicked an image file in Nautilus, the file opened in an existing instance of the GIMP, if it was already running.  Now, after I compiled and installed GIMP 2.6.10, a double-clicked file opens into a new instance of the program.  The same for files that are dropped on the GIMP icon in the panel.  The only way to avoid this behaviour is to switch to the running instance of GIMP and use the Open command.

I suspect there must be a setting for this somewhere, but my searches turned up zilch.  What can I do?

---

### Post by phreeky on 2010-08-29
Did you compile 2.6.10 yourself?

GIMP uses D-BUS to do this. You need libdbus-glib (and I guess the -dev package) installed. When you run the GIMP configure script prior to compiling you'll see it check for d-bus.

If your copy of GIMP is from the repos then I can only guess it isn't compiled with this, or perhaps you just don't have the libdbus-glib package installed (maybe it should be a dependency, I dunno).

---

