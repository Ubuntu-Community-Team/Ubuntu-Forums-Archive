---
title: "Xscreensaver disabled at shutdown?"
date: 2012-01-01
forum: Desktop Environments
---

### Post by onipar on 2012-01-01
I have Ubuntu 11.10 installed.  Yesterday I followed [this guide]("http://www.liberiangeek.net/2011/10/enable-screensavers-in-ubuntu-11-10-oneiric-ocelot/") in order to uninstall the Gnome screensaver (black screen) and install Xscreensaver.  Everything worked fine.  The first time I opened Xscreensaver, a dialog opened stating that it ws not running, and asked if I wanted to run it.  I said yes.  It worked all day.

This morning, when I restarted the system, I noticed the screensaver I had chosen did not go on, just the blank screen.  When I opened Xscreensaver, the dialog opened again, asking if I wanted it to run on this monitor (like the first time).  The exact message is as follows:  "The Xscreensaver Daemon doesn't seem to be running on display ':0'.  Launch it now?" 

So, I'm wondering if there's a way to keep Xscreensaver running even after shutdown?  I don't want to have to tell it to run every time I shut down.  

Thanks!  :D

---

### Post by onipar on 2012-01-02
Any ideas?  :)

---

### Post by onipar on 2012-01-02
Well, I solved it with a little help elsewhere.  Simple fix (and my own stupid fault).  I misspelled the xscreensaver command line in the start up applications.  So if anyone finds this thread searching for the same problem, I'd start there.  ;)

---

