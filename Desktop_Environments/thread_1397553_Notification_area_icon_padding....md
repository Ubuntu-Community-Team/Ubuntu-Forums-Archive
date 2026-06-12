---
title: "Notification area icon padding..."
date: 2010-02-03
forum: Desktop Environments
---

### Post by Izobalax on 2010-02-03
Hi!

I note that one of the modifications the Fedora devs did to the GNOME desktop for Fedora 12 is hack the notification area and add some 6 pixel or so padding around the icons. This, in my opinion, was very much needed, not just for functionality but also for aesthetics. 

[You can see a shot of what I mean here](https://fedoraproject.org/w/uploads/a/af/F12-relnotes-screenshot-main.png)

Is there a way of implementing this on Ubuntu?

/izo\

---

### Post by tgalati4 on 2010-02-03
Yes.  Modify the source code and recompile.

[http://ubuntuforums.org/showthread.php?t=1386621&highlight=notify-osd](http://ubuntuforums.org/showthread.php?t=1386621&highlight=notify-osd)

[http://ubuntuforums.org/showthread.php?t=1345040&highlight=notify-osd](http://ubuntuforums.org/showthread.php?t=1345040&highlight=notify-osd)

I recently installed Linux Mint 8 64-bit (based on Karmic) on a client's machine, and the vertical gap was already increased.  My modifications increase the horizontal gap as well, because you need access to the side scroll bars on maximized windows.  Notifications should never interfere with a user's interaction on the desktop.  It's annoying.

I have a *.deb file for jaunty, but it's on another machine at the moment.

Ignore this post.  It appears I screwed up.  The OP wants extra space between the system tray icons.

---

### Post by Izobalax on 2010-02-03
> **tgalati4 said:**
> Yes.  Modify the source code and recompile.

[http://ubuntuforums.org/showthread.php?t=1386621&highlight=notify-osd](http://ubuntuforums.org/showthread.php?t=1386621&highlight=notify-osd)

[http://ubuntuforums.org/showthread.php?t=1345040&highlight=notify-osd](http://ubuntuforums.org/showthread.php?t=1345040&highlight=notify-osd)

I recently installed Linux Mint 8 64-bit (based on Karmic) on a client's machine, and the vertical gap was already increased.  My modifications increase the horizontal gap as well, because you need access to the side scroll bars on maximized windows.  Notifications should never interfere with a user's interaction on the desktop.  It's annoying.

I have a *.deb file for jaunty, but it's on another machine at the moment.

Ignore this post.  It appears I screwed up.  The OP wants extra space between the system tray icons.


Haha, well thanks for the quick reply in any case! But yes, I'm asking about extra spacing between notification area icons. 

/izo\

---

### Post by Izobalax on 2010-02-06
Bumparoo!

/izo\

---

