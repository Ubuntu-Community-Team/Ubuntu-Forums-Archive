---
title: "Netbook remix toolbar disappears"
date: 2009-09-18
forum: Desktop Environments
---

### Post by MiRee446 on 2009-09-18
Disclaimer:  I'm a newb to Ubuntu

After attempting to install compiz and enable effects I managed to render my desktop unusable.  It was completely black until I deleted all instances of compiz from the command line.  

When I got everything somewhat functional I noticed that upon startup the top toolbar is completely gone (1st image).  And sometimes when I first get to the homescreen it pushes windows to the background.

I can get it to return by using the desktop switcher to switch to the classic desktop and then switching back to the remix desktop (2nd image).  Notice how some of the icons, namely the desktop icon on the right, changes.  Also, the toolbar briefly changes color as well.

Any ideas on how to fix this?

---

### Post by Brandon Williams on 2009-09-19
IIRC, you have to run the classic desktop if you want compiz and desktop effects. I don't think that UNR plays well with compiz. If you want to run UNR, I think you need to use metacity as your window manager.

---

### Post by MiRee446 on 2009-09-20
Yea i was using the classic desktop with compiz.  i deleted it and the toolbar in unr was still gone.  will installing metacity fix this problem?

---

### Post by Brandon Williams on 2009-09-20
If it's primarily the panel and associated functionality that's giving you problems, then I suggest you read [the release notes](http://www.ubuntu.com/getubuntu/releasenotes/904#Missing%20GNOME%20panels%20in%20Ubuntu%20Netbook%20Remix%20after%20using%20the%20desktop-switcher%20application). This is a well-known bug in Jaunty, with fixes described in the bug report that's referenced in the release notes.

In the future, you should either avoid using the desktop switcher or upgrade the desktop switcher with the version currently in the proposed repo.

---

