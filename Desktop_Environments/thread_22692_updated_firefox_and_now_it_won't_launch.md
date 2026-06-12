---
title: "updated firefox and now it won't launch"
date: 2005-03-29
forum: Desktop Environments
---

### Post by jnoreiko on 2005-03-29
I've updated Firefox to the latest version.
First of all I used Mozilla's own installer, as apt-get was complaining about broken packages. I got Firefox installed, but on launch it froze.
So I fixed my package problems, then with apt-get I removed firefox with apt-get, and reinstalled it. 

Launching it appears to do nothing.
Launching it from the command line gives this, over and over again:

(QFA)Talkback error: Can't initialize.
*** loading the extensions datasource
*** ExtensionManager:checkForMismatches: no access privileges to application directory!

And from a root command line, gives lots of this line:

*** loading the extensions datasource

---

### Post by jnoreiko on 2005-03-29
There were things left in the folders.
Another go an uninstalling and a few rms and reinstall and it works again. phew.

---

