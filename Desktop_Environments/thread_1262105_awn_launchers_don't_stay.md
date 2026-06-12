---
title: "awn launchers don't stay"
date: 2009-09-09
forum: Desktop Environments
---

### Post by blur xc on 2009-09-09
I read a post explaining how to add launchers via-drag'n'drop, but I can't find it anymore.  So, what I've done is right click an app from my menu and select add launcher to desktop.  then I drag and drop the launcher to my awn dock.  After that I deleted the launchers from my desktop- don't need them if they are on my dock, right?  Then, after a reboot or a logout/login, they go away and are listed as invalid launchers.

Previously, I was creating each launcher manually, which is a total pita.  Mostly the browsing for the correct icon part.

What gives?

Thanks,
BM

---

### Post by gwpritch on 2009-09-24
I'm having a similar problem so I thought I'd give this a bump.
When I first installed awn I created Launchers in the preferences dialog. They worked fine. After a reboot the launchers are gone from the dock although they are still listed in the dialog. Also icons do not appear on the dock when an app is started. All the applets appear and work fine. Anyone have any ideas? Thanks.

---

### Post by blur xc on 2009-09-24
> **gwpritch said:**
> I'm having a similar problem so I thought I'd give this a bump.
When I first installed awn I created Launchers in the preferences dialog. They worked fine. After a reboot the launchers are gone from the dock although they are still listed in the dialog. Also icons do not appear on the dock when an app is started. All the applets appear and work fine. Anyone have any ideas? Thanks.

I *think* I solved my problem-  What I needed to do, for the drag and drop of the launchers to stay put, is to not delete the desktop icons that I dragged to the AWN dock.  So, inside of my home folder, I created a .awn sub-folder (a hidden folder) and moved all the launchers there.  Then from that folder, open in nautilus, I dragged them to the awn dock.  Now everything seems to be fine.

I still think it acts a bit goofy sometimes.  Maybe sometine I'll get around to tinkering w/ cairo dock.

BM

---

### Post by ST3ALTHPSYCH0 on 2009-10-08
You should be able to drag directly onto the AWN "glass" pad. It'll show a little plus symbol in the corner of the icon if you're somewhere you can drop it. I drag it to the side of the AWN launcher where you can't drop anything to make sure that I'm over the Launcher properly (that way I can watch the plus sign come back, b/c I kept letting go of the mouse button and my shortcuts would fly back to its original location)

---

### Post by tacantara on 2009-10-08
> **blur xc said:**
> 
I still think it acts a bit goofy sometimes.  Maybe sometine I'll get around to tinkering w/ cairo dock.

BM

I've been using Cairo Dock, and I find the drop & drag from menus, etc. to work very well.  Besides, I personally find it a bit easier to work with than AWN.  It may be worth your time to try it out.

JMO

---

