---
title: "wireless connection icon"
date: 2019-09-03
forum: Desktop Environments
---

### Post by tendouser on 2019-09-03
wifi icon in XFCE is duplicated every system start!

---

### Post by &amp;KyT$0P# on 2019-09-03
This happens to me sometimes.  I deal with it by having the panel Notification Area preferences set to hide the duplicate icon.

You can also try running this in Terminal -
```
killall -s SIGINT nm-applet && nm-applet &
```

---

### Post by speartip on 2019-09-05
Kind of annoying isn't it. It's been a known issue in xfce for a long time. Hope it's fixed in the next LTS, which will be running xfce 4.14.
Often logging out & back in again fixes it.

---

