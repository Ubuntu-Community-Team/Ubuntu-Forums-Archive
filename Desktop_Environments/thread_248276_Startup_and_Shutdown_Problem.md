---
title: "Startup and Shutdown Problem"
date: 2006-08-31
forum: Desktop Environments
---

### Post by TheKnight on 2006-08-31
Hi, I installed kubuntu on my computer a few weeks ago and have liked it a lot.  I have had many problems but have fixed most of them.  I currently have several problems that I do not know how to go about fixing.  

1. When I start up, kubuntu will hang on checking harddrives.  It switches into the commandline interface and says that the check is done, but the [ok] doesn't appear.  I have to hard-shutdown.  However, if I open the cd drive while booting up, my system starts up just fine.  I still have problems with the drive empty and closed, though.  

2. When shutting down, kubuntu hangs on "Stopping bluetooth" even though I have no bluetooth devices, and have never had any.  I saw some posts that said bluetooth could be disabled on startup by doing:
   sudo chmod -x /etc/init.d/bluez-utils
and then adding
   alias bluetooth off
   alias rfcomm off
   alias l2cap
to /etc/modules.d/bad_list
Unfortunately, I don't seem to have an /etc/modules.d/ directory.  The post I saw was about ubuntu, but from a quick google it seems like kubuntu should have that directory as well, which is slightly disturbing.

How can I fix these problems?

Thank you for taking the time to read this.

---

