---
title: "update &quot;not authenticated&quot;"
date: 2006-01-09
forum: Desktop Environments
---

### Post by tjd on 2006-01-09
The most recent update I've been notified of via the automatic updater tells me that it the two files it wants to install, "info" and "sudo", have not been authenticated.

With sudo especially, I don't want to take any chances. Can someone help me verify the files, or find out what's going on?

Toby

---

### Post by Ampersand on 2006-01-09
Unless you've added any unofficial repositories to your /etc/apt/sources.list file, there shouldn't be a problem. If you right click on the package in Synaptic and go to Preperties, then the Versions tab, you can find out where it's coming from.

The message is generally nothing to worry about, though.

---

