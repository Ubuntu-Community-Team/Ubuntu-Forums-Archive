---
title: "Xfce screensaver not using my settings"
date: 2009-02-22
forum: Desktop Environments
---

### Post by fisherm on 2009-02-22
I am using 8.04.2 and have both GNOME and Xfce available as sessions. In GNOME my screensaver follows the settings I input. In Xfce, however, when I use the screensaver settings menu it doesn't affect how the screensaver works. (i.e. In Xfce I have it set to come on as a blank screen screensaver after 5 minutes, but instead it takes about 10 minutes and when it launches it uses a random screensaver instead of the blank screen.) Anyone know why this happens or how to have Xfce "obey". Not that the screensavers aren't pretty, I'm just particular about my blank screen. FWIW it also doesn't matter if I try to deactivate the screensaver, it still comes on. Thanks in advance.

---

### Post by kellemes on 2009-02-22
> **fisherm said:**
> I am using 8.04.2 and have both GNOME and Xfce available as sessions. In GNOME my screensaver follows the settings I input. In Xfce, however, when I use the screensaver settings menu it doesn't affect how the screensaver works. (i.e. In Xfce I have it set to come on as a blank screen screensaver after 5 minutes, but instead it takes about 10 minutes and when it launches it uses a random screensaver instead of the blank screen.) Anyone know why this happens or how to have Xfce "obey". Not that the screensavers aren't pretty, I'm just particular about my blank screen. FWIW it also doesn't matter if I try to deactivate the screensaver, it still comes on. Thanks in advance.

Probably because you're configuring the Gnome screensaver from XFCE, this while XFCE normally uses [xscreensaver]("http://www.jwz.org/xscreensaver/") as far as I know.
From commandline..
```
xscreensaver-demo
```
Now configure this one, or disable it if you wish.
By the way, I always found xscreensaver the best one, there are a lot of screensavers available and you can use it from every environment.

---

### Post by fisherm on 2009-02-22
Exactly what I needed! Thanks for the help. Now to find a way to make the screensaver settings button in the settings manager open xscreensaver-demo...I am a man on a mission.

---

### Post by kellemes on 2009-02-22
> **fisherm said:**
> Exactly what I needed! Thanks for the help. Now to find a way to make the screensaver settings button in the settings manager open xscreensaver-demo...I am a man on a mission.

Can't help you there.. I'm on another environment.

---

