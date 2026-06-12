---
title: "Error message starting GNOME in remote XDMCP session"
date: 2008-07-17
forum: Desktop Environments
---

### Post by I Use Dial on 2008-07-17
I'm running a fresh install of Ubuntu 8.04 for AMD 64 and when trying to start a remote session through login screen of a different Ubuntu 8.04 machine (also fresh install) or through Xming in Windows XP, I get the following message after waiting a very long time:

There was an error starting GNOME settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply.  Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

---

### Post by jim-g on 2008-08-18
I'm having the same thing happening.  The error msg said the bus security is blocking the reply as well.  Being new to Linux and Ubuntu, I have a problem with trying to trouble shoot it.  After the long bootup the GUI seems to work alright though.

Since original posting I found where someone recommended going to SYSTEM+Administration+Network  and selecting 'localhost'     

IT WORKED!  Removing other host entries and leaving only the localhost did it for me.

 Jim-G
Thanks for your input.

---

