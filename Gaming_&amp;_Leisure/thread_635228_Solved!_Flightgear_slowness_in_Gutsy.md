---
title: "Solved! Flightgear slowness in Gutsy"
date: 2007-12-08
forum: Gaming &amp; Leisure
---

### Post by wheelhorse2347 on 2007-12-08
Now, I can't say that this will work for everyone.  I'm fairly new to Linux.  I just installed Gutsy (AMD 64) on my computer, got all the correct drivers, and yet Flightgear only ran at about one frame per second.  After playing around with it for a little bit, this is what I came up with.

1.  Have the most recent drivers
2.  Use "glxinfo |grep rendering" in terminal to make sure your direct rendering is on.  (The value should be 'yes')
3.  Enter "gksudo gedit /etc/X11/xorg.conf" into terminal and scroll down until you find where it says Section "screen"
4.  Change your default depth to 16
5.  Save file, and try flightgear.

I am not saying this will work for everyone.  I am just saying that this has seemed to work for me.  Now, flightgear is running flawlessly with no freezes.

Hope it works for you!
Wheelhorse2347

---

