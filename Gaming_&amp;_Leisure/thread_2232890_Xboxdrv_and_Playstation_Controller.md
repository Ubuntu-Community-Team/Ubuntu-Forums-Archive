---
title: "Xboxdrv and Playstation Controller"
date: 2014-07-04
forum: Gaming &amp; Leisure
---

### Post by Marshall_Mason on 2014-07-04
I went to Wal-Mart one day and got a cheap PS3 controller for $14. I like the controller, but it I have been struggling to get it to work on my Ubuntu laptop. Xboxdrv runs and recognizes the controller perfectly, but whenever the controller is set up it moves and manipulates the mouse and its scroll wheel with the analog sticks. I would like to have Xboxdrv treat the analog sticks like they would normally be treated with if I had a normal plug and play controller

---

### Post by Ranko Kohime on 2014-07-05
You might try removing the package "xserver-xorg-input-joystick" if it's installed on your system.

```
sudo apt-get remove xserver-xorg-input-joystick
```

Not guaranteed to work, but that's been the issue most of the times I've had this happen to me.

---

