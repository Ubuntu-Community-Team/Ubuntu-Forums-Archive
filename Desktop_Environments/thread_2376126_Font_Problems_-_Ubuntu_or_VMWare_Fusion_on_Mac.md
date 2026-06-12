---
title: "Font Problems - Ubuntu or VMWare Fusion on Mac?"
date: 2017-10-30
forum: Desktop Environments
---

### Post by redwullf on 2017-10-30
Seeing some font weirdness. Ubuntu version 17.10 (have noticed this in prior versions as well), running on VMWare Fusion 8.5.8 on a new iMac on macOS High Sierra 10.13. Examples include right-click menu on desktop items, like Trash:

[IMG]http://i718.photobucket.com/albums/ww182/redwullf/ubuntufont1.png[/IMG]

And most commonly in Google Chrome, especially in Google Docs:

[IMG]http://i718.photobucket.com/albums/ww182/redwullf/ubuntufont2.png[/IMG]

That's not "censored" text in those cells, that's how it actually displays. Font appears fine when entering into cell, but as soon as I enter or click out, it looks like black blocks. 

Thoughts? Is this a Google Chrome issue (as, ironically, Google Docs appear fine in a NON-Chrome browser, like Firefox), a VMWare Fusion issue, or an Ubuntu issue? I'd say it was new with 17.10, but as I've said, I've noticed this for quite some time now.

---

### Post by ajgreeny on 2017-10-30
Try booting into an X11 session instead of wayland, assuming the mac system has that option the same as a standard PC, and that both are available in VMware, to see if wayland is perhaps the problem.

---

