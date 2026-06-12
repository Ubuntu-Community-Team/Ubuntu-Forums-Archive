---
title: "icewm screen resolution problems"
date: 2005-11-25
forum: Desktop Environments
---

### Post by eric0919 on 2005-11-25
I recently tried to convert my parents old Compaq P3 over to Ubuntu but don't seem to be able to get any resolution above 800x600.  In windows I can use both 800x600 and 1024x768.  The system has integrated video and only 128mb of system memory.  I did a server intsall and followed the mini-ram how-to.  I have changed the config file in etc/X11 to have only 1024x768 but nothing seemed to change.  the screen just looks very bad.  The fonts are fuzzy and hard to read.  I tried doing sudo dpkg-reconfigure xserver-xfree86 but I had no idea what to put for most of the questions.

any help is appreciated.

thanks Eric

---

### Post by aysiu on 2005-11-26
I'm no screen resolution expert, but [this link](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) has just about every screen resolution fix I've ever seen.

For me, it was the HorizSync and VertRefresh that did it.

---

