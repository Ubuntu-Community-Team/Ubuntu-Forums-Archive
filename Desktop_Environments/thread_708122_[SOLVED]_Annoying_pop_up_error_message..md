---
title: "[SOLVED] Annoying pop up error message."
date: 2008-02-26
forum: Desktop Environments
---

### Post by johnnyhop on 2008-02-26
My annoying pop up message is "Could not find mime type--application/octet-stream."  This began to occur after experimenting in Wine, after the pop up occurred tried removing the change in properties but to no avail.  It comes up repeatedly when KDE starts when closing 5 instances the desktop icons appear, then 5 more instances get closed the panel icons appear.  The message also pops up when opening Dolphin as well as  some other apps and makes doing a file search in Dolphin impossible.  I noticed Azmodan posted getting this  same error message on 5/30/2007 and it appears no one was able to help.  If this is a mystery to the experts I'll perform a format and reinstall of the file system and if before I'm to continue to mess around when not sure what I'm doing, research how to create an image of the file system.  Its sure handy to have home on a separate partition!

---

### Post by FrozenFox on 2008-02-26
Load kcontrol, go to KDE components, go to file associations, click at the bottom to add a new one. put it under the applications category, name it octet-stream. Now go to this in this list after it's made, click on the embedding tab, and set it to "use settings for application group" and check the checkbox. Every time I got that error, i just added the entry with the correct settings back, and everything was ok

---

