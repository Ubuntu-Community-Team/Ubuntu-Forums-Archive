---
title: "Xfce screensaver starts while playing video"
date: 2011-08-02
forum: Desktop Environments
---

### Post by ziekfiguur on 2011-08-02
I recently switched to using xfce. Since then, every time i'm watching a video the screensaver turns on after 10 minutes. 
Is it possible to disable this behavior when playing a video, but still have the screensaver activate when i'm not doing anything?
I'm starting to get really annoyed, as i don't have a tv, i use my pc for everything.
I don't know if it matters, but i'm using mplayer
Any suggestion would be appreciated.

---

### Post by haresear on 2011-08-02
In a terminal window, the command "xset -dpms" works for me (thanks to hhh).
Then "xset +dpms" to turn display power management back on.

More options:
[http://ubuntuforums.org/showthread.php?t=1810262&highlight=screensaver](http://ubuntuforums.org/showthread.php?t=1810262&highlight=screensaver)

---

### Post by ziekfiguur on 2011-08-03
`xset -dpms' doesn't work here, and neither do `xset s noblank' and `xset s off'
Any other ideas?

---

### Post by haresear on 2011-08-03
> **ziekfiguur said:**
> `xset -dpms' doesn't work here, and neither do `xset s noblank' and `xset s off'
Any other ideas?

Have you unchecked the screensaver and display power management in the screensaver settings GUI?

You might look at the other xset options via "man xset". A couple of other possiblities suggested by the manual:

> xset dpms off
> xset dpms force off

---

