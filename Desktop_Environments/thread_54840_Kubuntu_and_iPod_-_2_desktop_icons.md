---
title: "Kubuntu and iPod - 2 desktop icons"
date: 2005-08-06
forum: Desktop Environments
---

### Post by windi on 2005-08-06
So today I switched over to Kubuntu KDE from Ubuntu GNOME, and whenever I plug in my iPod, 2 desktop icons appear, the one that should be there and one to the iPod's firmware partition. GNOME only displayed one icon, it skipped the firmware partition, like it should.

Is there some way to get KDE to do the same?
I'm guessing this has something to do with DBus and HAL.

---

### Post by daller on 2005-09-04
You can add an applet to the panel, and disable the filesystem-icons on your desktop.

Rightclick the panel, and choose: Add to panel -> Panelapplication -> Storage media...

Then you rightclick the applet, and choose configure!

Now click "Media" and unmark the partitions that you dont want to be showed - I'm afraid there is no solution to the desktop-thing ATM...

---

