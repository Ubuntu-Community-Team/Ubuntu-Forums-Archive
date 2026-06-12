---
title: "Incorrect cursor movement across X displays"
date: 2013-09-06
forum: Desktop Environments
---

### Post by chris41 on 2013-09-06
Good morning all, 

I have a display wall consisting of 18 monitors connected to three ATI Eyefinity 6 6800 cards.  I'm using the ATI proprietary drivers and have setup three Eyefinity display clusters of six monitors each (one connected on each card).  Xinerama is turned off, so I essentially get three X displays. The diagram below shows my setup.

When I start X, the cursor is on display :0, but if I move to the right (towards display :0.1), it moves onto :0.2 instead.  Once on display :0.2 I can't get it off again, it just wraps around.  My only option is to restart X.

Any suggestions as to what the problem may be?

Many thanks.
[IMG]http://i.imgur.com/9BBiKlx.png[/IMG]

---

