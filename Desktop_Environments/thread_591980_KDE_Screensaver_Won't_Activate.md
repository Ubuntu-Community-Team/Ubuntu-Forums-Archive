---
title: "KDE Screensaver Won't Activate"
date: 2007-10-25
forum: Desktop Environments
---

### Post by ben::zen on 2007-10-25
So, I upgraded to Gutsy. Now, not only will my monitor take far longer than the 15 minutes I specify to power off, the screensaver will never activate. Also, related, I believe, is that the suspend to RAM function, which I have set for a 15-minute wait, will also not activate. Is there any real error output I could post?

---

### Post by TeaSwigger on 2007-10-26
In /etc/X11/default-display-manager, is it using GDM or KDM? Just a stray thought, might not be related.

---

### Post by ben::zen on 2007-10-26
> **TeaSwigger said:**
> In /etc/X11/default-display-manager, is it using GDM or KDM? Just a stray thought, might not be related.
/usr/bin/kdm --I'm not sure it's related.
Also, I should mention I've started using the BOINC manager for World Community Grid.

---

### Post by 67GTA on 2007-10-28
Try this:

[http://forums.debian.net/viewtopic.php?t=13487&highlight=screensaver](http://forums.debian.net/viewtopic.php?t=13487&highlight=screensaver)

---

