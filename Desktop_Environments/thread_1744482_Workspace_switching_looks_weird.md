---
title: "Workspace switching looks weird"
date: 2011-04-30
forum: Desktop Environments
---

### Post by b0wter on 2011-04-30
I've made a complete fresh install of Ubuntu 11.04 (been using 10.10 before) and I noticed that the workspace switching looks like it was back in 8.10 or earlier.

It's hard to explain but in the newer versions it always looked like only the application windows were moving when switching the workspace. The panels and background image stood still.
But after the new installation it looks like everything is moving, the panels, the background, popup notifications and so on (just like in the old ubuntu versions).
This happens to me both with gnome 2.x and Unity. Any ideas what settings I have to adjust?
(This happened to me as a bug in 10.10 a couple of time but back then I simply opened the appearance settings, clicked the now missing visual effects tab and simply dis- and reenabled the effects)

---

### Post by Krytarik on 2011-04-30
That is just because of an obviously missing default setting.

Set "CompizConfig Settings Manager -> Desktop Wall -> Viewport Switching -> Non Sliding Windows" to:
```
type=Dock | type=Desktop | state=Sticky
```Greetings.

---

### Post by mc4man on 2011-04-30
look here for what to add to the text box in Desktop Wall > Viewport Switching
[http://ubuntuforums.org/showthread.php?t=1742298](http://ubuntuforums.org/showthread.php?t=1742298)

edit  - shown above

---

### Post by b0wter on 2011-05-01
Thanks a lot. I like my desktop a lot more now :]

---

