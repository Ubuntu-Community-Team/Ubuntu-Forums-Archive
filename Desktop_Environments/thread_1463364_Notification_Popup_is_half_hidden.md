---
title: "Notification Popup is half hidden?"
date: 2010-04-26
forum: Desktop Environments
---

### Post by rEgonicS on 2010-04-26
Hello, I've been using Ubuntu 9.10 on my laptop for a couple weeks now and its been running great! I have one thing that really nags me though, the notification popup on the top right of the desktop that pops up when you receive an instant message or changes songs is always half hidden. Anyone know of a solution?

[IMG]http://i40.tinypic.com/2u4ljci.png[/IMG]

It's the black bubble on the top right of the right monitor.

---

### Post by quantumstitch on 2010-04-26
Please post a screenshot.

---

### Post by 3rdalbum on 2010-04-27
Are you running dual-monitor?

The following piece of information might help:

> You can use the gconf-key "/apps/notify-osd/gravity" set to 2 and set "/apps/notify-osd/multihead_mode" to "focus-follow" that way you'll see notification-bubbles being displayed in the visible area.

Those Gconf keys might not already exist, but you can create them in "gconf-editor".

---

### Post by rEgonicS on 2010-04-27
Thanks for the replies! I was playing around with 3D cube effects and it turns out that if the height of the 2 monitors are different, instead of creating 2 "rectangles" side by side, it creates one big rectangle and fills the gap created by the smaller monitor with empty space. Some applications like conky and the notification popup reside in that empty space.

---

