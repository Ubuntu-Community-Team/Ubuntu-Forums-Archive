---
title: "X11vnc fails when no screen is connected"
date: 2017-04-02
forum: Desktop Environments
---

### Post by izznogooood on 2017-04-02
I've set up X11vnc to run as a daemon. It works well except when i have no screen connected to the computer. X11vnc then gets stuck in a loop where it doesnt fin a screen (understandable), 

Is there a way around this?

---

### Post by deadflowr on 2017-04-03
Install the xserver-xorg-video-dummy package.
A fine guide to start
[https://ubuntuforums.org/showthread.php?t=1832456]("https://ubuntuforums.org/showthread.php?t=1832456")
Hope it helps

---

### Post by izznogooood on 2017-04-03
I'm sure it will, thanks.

---

