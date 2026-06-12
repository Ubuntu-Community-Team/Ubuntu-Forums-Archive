---
title: "Menu Bar missing in Xubuntu-desktop"
date: 2011-12-27
forum: Desktop Environments
---

### Post by kvvv on 2011-12-27
Hello,

I installed Ubuntu 11.10, didn't like it so I installed xubuntu-desktop.

Today, for some reason, the menu bars just disappeared from gedit, gvim, firefox, gnome-terminal and everything else.

I might have done something, but I really don't remember doing so. Any suggestions as to what could have happened, and how to get it back? Logging in and out didn't help.

I am pretty much handicapped without this. It worked with KDE, but then KDE sucks on my hardware for some reason.

---

### Post by neu5eeCh on 2011-12-27
Yes, this is a known bug:

Look [here]("http://ubuntuforums.org/showthread.php?t=1846266"). The developers of XFCE claim the bug will be dealt with in 12.04.

---

### Post by kvvv on 2011-12-27
> **VTPoet said:**
> Yes, this is a known bug:

Look [here]("http://ubuntuforums.org/showthread.php?t=1846266"). The developers of XFCE claim the bug will be dealt with in 12.04.

That didn't solve my problem. My window manager is working fine, AFAIK. It's the menu bars which disappeared.

---

### Post by Toz on 2011-12-27
I believe this has something to do with the unity global menu not having anywhere to display the menu bars in xfce. Try uninstalling **indicator-applet-appmenu**.

---

### Post by neu5eeCh on 2011-12-27
> **kvvv said:**
> That didn't solve my problem. My window manager is working fine, AFAIK. It's the menu bars which disappeared.

Ah... my bad, then. You're in good (and much better) hands with Toz.

---

### Post by kvvv on 2011-12-28
> **Toz said:**
> Try uninstalling **indicator-applet-appmenu**.

Didn't help :confused:

Edit: I removed the indicator-appmenu and the indicator-applet-complete packages, and it now works. My Unity session is probably broken now though. But meh, I can live without it.

Thanks!

---

