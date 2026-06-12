---
title: "Preventing multiple instances."
date: 2013-01-09
forum: Desktop Environments
---

### Post by yizrahomme on 2013-01-09
Hi,
Is there a way to stop programs like Chrome and Terminal (specifically xfce4-terminal) from opening multiple instances?

If I have an instance of the terminal running, and forget to look for it at the top of the screen on the bar, and click instead on the icon on the launcher at the bottom, it immediately opens a new instance.

I want it to (by default) bring the already open instance to focus, and only open a new one if I do middle-click on the launcher icon and select 'new instance' (or whatever).

Thanks.

---

### Post by Toz on 2013-01-09
This functionality doesn't exist OOB in xfce. However, we had a discussion about this recently over on the Xfce boards and I threw together a launcher script that addressed this. Have a look at this link: [http://forum.xfce.org/viewtopic.php?id=6168]("http://forum.xfce.org/viewtopic.php?id=6168"). The final version of the script is at the end of the thread, but information about how it works exists throughout the thread.

---

### Post by LewisTM on 2013-01-09
One way to stop launching multiple instances is to use a third-party dock like Cairo-Dock or Docky. A dock's launcher icons get reused as running application task buttons.

You could take a similar approach with the old xfce4-taskbar-plugin. This is also meant to replace the window buttons plugin in your panel. The plugin shows icons for current tasks which can be "pinned" to become launchers themselves, a bit like the Windows 7 taskbar. The plugin is not part of current Xfce packages. There was a recent [attempt]("http://ubuntuforums.org/showthread.php?t=2090875") to revive it, with some success.

Cheers!

---

### Post by yizrahomme on 2013-01-10
> **Toz said:**
> This functionality doesn't exist OOB in xfce. However, we had a discussion about this recently over on the Xfce boards and I threw together a launcher script that addressed this. Have a look at this link: [http://forum.xfce.org/viewtopic.php?id=6168]("http://forum.xfce.org/viewtopic.php?id=6168"). The final version of the script is at the end of the thread, but information about how it works exists throughout the thread.

Just checked out your script, and can't test it at the moment, but it looks very much like what I need.  Thank you very, very much, and I shall get that tested when I get back from work this evening. :-)

---

### Post by yizrahomme on 2013-01-10
> **Toz said:**
> This functionality doesn't exist OOB in xfce. However, we had a discussion about this recently over on the Xfce boards and I threw together a launcher script that addressed this. Have a look at this link: [http://forum.xfce.org/viewtopic.php?id=6168]("http://forum.xfce.org/viewtopic.php?id=6168"). The final version of the script is at the end of the thread, but information about how it works exists throughout the thread.

Blimey, it works!  Well *done* Sir!  Thank you!

---

### Post by markbl on 2013-01-10
> **yizrahomme said:**
> Hi,
Is there a way to stop programs like Chrome and Terminal (specifically xfce4-terminal) from opening multiple instances?


You could use Unity or Gnome Shell as that is how they work by default.

---

### Post by yizrahomme on 2013-01-11
> **markbl said:**
> You could use Unity or Gnome Shell as that is how they work by default.

Unity is about the ugliest thing I have ever seen.  I haven't used Gnome for a while, but last time I did, it was very big, and very slow.

---

