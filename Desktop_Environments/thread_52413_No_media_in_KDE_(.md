---
title: "No media in KDE :("
date: 2005-07-27
forum: Desktop Environments
---

### Post by kLy on 2005-07-27
Hey

I have dbus-1 installed and all the needed kde libs (I think). But I it doesn't automount the cd like it should. Also, there is nothing in media:/ and if I add the storage manager to kicker, I get the message "KDE mediamanager is not running".

Is there some package I missed installing? :(

Thanks

---

### Post by kLy on 2005-07-27
hmm... i seem to have somehow fixed it. I did a dpkg-reconfigure kdelibs and kdebase since I only installed dbus after kde. don't know if that's what did it

---

### Post by vivedekananda on 2006-03-21
I had similar problem, after some misconfiguration,
the reason is that kded was not running.

---

