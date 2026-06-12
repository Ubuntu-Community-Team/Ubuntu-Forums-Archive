---
title: "Notification bubbles are offscreen"
date: 2012-01-09
forum: Desktop Environments
---

### Post by Reded on 2012-01-09
Hey all, I've been having this problem a while and I'm pretty stumped on how to fix it.

My notification bubbles are too high up, on my screen I only get the bottom bit of them, so I can't read the text in them. 

I have two monitors, and the bubbles appear on the right-hand side monitor, while the Unity panel appears on the left.

I'm using 11.10, 64-bit. I'm not sure what other info I can give, so if anymore info is needed do ask.

I've attached a screenshot of my right screen so you can see it, in case the thread didn't make any sense ;)

Thanks in advance!

---

### Post by Krytarik on 2012-01-09
This is the related bug report:

[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/716458](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/716458)

One workaround, like also mentioned in comment #6 there, would be to place the notifications somewhere else, better fitting; bottom-right, for example, or on the (left) side/screen where the Unity Launcher is too, but there they would likely end up covering the Launcher, and this way get in your way occasionally.

[http://www.tuxgarage.com/2011/06/tweaking-notify-osd.html](http://www.tuxgarage.com/2011/06/tweaking-notify-osd.html)

Another workaround - if you are using the regular Unity, *not* 2D - is mentioned in comment #8 of the bug report, but I cannot check that or confirm if that works since I'm not running one of the recent versions of Ubuntu (but Lucid 10.04) and have no multi-monitor setup.

Regards.

---

### Post by Reded on 2012-01-09
Hmm, so it's a bug - I'll have a play with those workarounds see what I can do, thanks for the post!

EDIT: Had a bit of a play with that notify-OSD tweaking patch thing - There was a setting in the GUI to change the horizontal/vertical positioning of the bubble, I just set it to 30 pixels down instead of 5, worked a treat! Now I don't need to move it across to the left-side of my other screen or anything like that, thanks for showing me that :D

I've also set the bubbles to disappear when clicked, which is something I've been wanting to do for a while too.

Thread solved - thanks again.

---

