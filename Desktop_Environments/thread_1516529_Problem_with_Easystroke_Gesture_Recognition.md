---
title: "Problem with Easystroke Gesture Recognition"
date: 2010-06-23
forum: Desktop Environments
---

### Post by gingivere0 on 2010-06-23
Whenever I try to perform a gesture with easystroke, black blocks take up a large area of the screen, making it so that I cant see anything underneath them until I stop performing the gesture.  It didn't used to be like this, before the gesture would perform mostly flawlessly.  I don't know what I did to cause it to start malfunctioning, but I would really like it to stop.  Thanks for all replies :)

[[IMG]http://img4.imageshack.us/img4/930/screenshotwu.th.png[/IMG]](http://img4.imageshack.us/i/screenshotwu.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by gingivere0 on 2010-06-24
Bump

---

### Post by gingivere0 on 2010-06-25
Bump, anyone have any ideas?

---

### Post by stinkeye on 2010-06-25
I've tried to reproduce what your seeing by changing a few things but still works as normal.
Are you running compiz ?
Video card and driver?
Is that conky or screenlets running on your desktop?

---

### Post by gingivere0 on 2010-06-25
Yes I am running compiz, and it's conky.  I think my video card is Intel Mobile Chipsets, or something similar.  And I don't know what my driver is.

---

### Post by stinkeye on 2010-06-25
The only thing I can suggest is try some different settings
eg turnoff conky
 change the way the way the gesture is drawn (default or compiz annotate plugin)
 If you switch to metacity does the error occur?


Even try setting up a new user account and see if the error is replicated.

---

### Post by gingivere0 on 2010-06-25
The problem must be with compiz, because whenever I switch to metacity, the program works as desired.

---

### Post by gingivere0 on 2010-06-25
AHA! I figured out what I had done wrong.  In compiz, under the wallpaper settings, I had it set so that the fill color was black. Disabling the wallpaper plugin made the black splotches go away. :DD Thanks for the help :)

---

### Post by stinkeye on 2010-06-25
Good to see you got it sorted. Was about to form a plan of attack. ):P

---

