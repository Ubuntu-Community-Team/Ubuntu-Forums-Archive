---
title: "[SOLVED] No sound in Fluxbox or Xubuntu"
date: 2008-01-09
forum: Desktop Environments
---

### Post by cmittle on 2008-01-09
I just install fluxbox recently and also Xubutu as alternate desktop environment/window manager.  I just realized today that there was no sound when I was in fluxbox.  I ctrl alt backspaced and logged into Xubuntu, same.  This seems to be linked to the problem I've been having with the gnome environment loading appropriately, because when I logged out of Xubuntu I logged into a GNOME session and the same problem I've described [here]("http://ubuntuforums.org/showthread.php?t=655978") occurs.  This was fixed in the same way I fix that problem, restart a time or three and the sound works and the gnome environment loads the toolbars.  Is there a particular gnome based feature that may be failing and depriving all of my sessions from playing sound, and also not allowing the gnome toolbars and desktop to load?

I would appreciate any help I can get.

Thank you,
Cory

---

### Post by mali2297 on 2008-01-10
Do you mean that you can't play music files or that you don't hear startup sounds et cetera?

Copy/paste this into the terminal:
```

aplay -vv /usr/share/firefox/res/samples/test.wav

```
Do you hear anything?

---

### Post by cmittle on 2008-01-13
I just backed up all of my stuff to the server I built on Thursday and reinstalled Ubuntu 7.10 on my laptop, and I no longer have this problem or the startup problem referenced in the other thread.  

Thank you,
Cory

---

### Post by BeardlessForeigner on 2008-01-13
In regard to this, I found that in a fluxbox install on top of Ubuntu I need all the gnome stuff to load in order to get sound and my volume buttons on my t43 to work. This of course also loads your Ubuntu GTK theme, etc. A common solution seems to be adding gnome-settings-daemon to your startup apps in fluxbox.

---

