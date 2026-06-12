---
title: "twinview troubles on second screen"
date: 2009-01-01
forum: Desktop Environments
---

### Post by whitto on 2009-01-01
Hello,
I have nvidia GeForce 6600 graphic card and use two monitors. They are different sizes and different resolutions. I manage extended desktop in TwinView mode. 
My desktop is Kde 4
The problem is, that I cannot put kde widgets on second monitor and also background appears strange. I have often (but not always) problems with rendering menus and other KDE widgets.
Attachment "Desktop2.jpeg" shows that background is not rendered on second display (I blurred desktop icons).
Attachments "Desktop3.jpeg" and "Desktop4.jpeg" show some wrong renderings.

On Attachment "Desktop.png" you can see how background is rendered sometimes. With black line I marked what is the visible part of display. Resolution of monitor is 1024x768, but the size of desktop is 1024x1024. Funny is, that I can move mouse on non visible area.

If I enable xinerama in xorg.conf background looks better, but I do not like that choice, because Windows would get strecched upon both screens when maximised.


Can anyone help me?

---

### Post by whitto on 2009-01-06
I resolved some of the troubles.
Installed compiz and emerald and when replaced desktop with those two, my desktop works as should. Now I can place plasma widgets on second screen and dragging window on non-visible area is blocked.
I can still move mouse on non-visible area and sometimes refreshing plasma widgets still fail.

---

