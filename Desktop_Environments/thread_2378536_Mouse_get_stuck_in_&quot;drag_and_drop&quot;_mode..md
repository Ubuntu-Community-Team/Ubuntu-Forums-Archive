---
title: "Mouse get stuck in &quot;drag and drop&quot; mode. When using touchscreen"
date: 2017-11-24
forum: Desktop Environments
---

### Post by karapetyan.s on 2017-11-24
Lubuntu 14.04

Touchscreen: (MasterTouch MT-500 USB), supports only single touch. 
Mouse not connected.
problem appears in next apps:
- Chromium: 62.0.3202.75
- Firefox 28.0

Touchscreen support only single touch. All touches in Chromium passes as "MouseDown" and "MouseUp" And sometimes "MouseUp" just not firing:
[https://prnt.sc/hen0c6](https://prnt.sc/hen0c6)

after that mouse get stuck in "MouseDown" state and left button click just stop working. (Right button click works fine).

I close Chromium or Firefox with ALT+F4
but mouse still stuck in "MouseDown" state _systemwide_ :
[https://www.dropbox.com/s/bf57bg47f3zsq2m/test.mp4?dl=0](https://www.dropbox.com/s/bf57bg47f3zsq2m/test.mp4?dl=0)

Even if I connect the mouse to the computer and disconnect touchscreen controller - the left mouse button will not work, until reboot.

But in mtpaint for example problem never occurs! There is some difference in how mtpaint and (chromium, firefox) works with mouse events?



I need touchscreen on this machine and I can't disable it because this will make the whole system unusable.

Any ideas? ](*,)

---

### Post by jeremy31 on 2017-11-24
I think Lubuntu 14.04 is EOL, have you tried Lubuntu 16.04?  The newer kernel may help

---

