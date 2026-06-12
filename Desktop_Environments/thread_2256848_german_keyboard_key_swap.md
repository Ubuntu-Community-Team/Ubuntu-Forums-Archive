---
title: "german keyboard key swap"
date: 2014-12-15
forum: Desktop Environments
---

### Post by geohei on 2014-12-15
Hi.

Should be easy, but I didn't find the solution so far.

I use a german Macintiosh keyboard with Ubuntu 14.04 desktop. All works fine, except that the keys "°^" (2nd row from top, 1st key) and "><" (5th row from top, 2nd key) are swaped.

Why is this?
How can I revert it?

Thanks,

---

### Post by beep3 on 2014-12-23
You can run **xev** from the command line to find the keycode of the keys and **xmodmap** to swap them. There's a very detailed explanation on [Ubuntu Aswers]("http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys-or-devices/24930#24930").

---

