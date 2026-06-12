---
title: "desktop effect"
date: 2008-03-08
forum: Desktop Effects &amp; Customization
---

### Post by xylon89del on 2008-03-08
I have downloaded and installed the ccsm.
and,i have enabled the restricted driver:Radeon Xpress 200M Series,
but then,when right click at the desktop and select" change desktop background" and go to the"visual effects" setting and try to select "custom"
But,it states that "The composite extension is not available".

---

### Post by jan quark on 2008-03-09
install this package

```
sudo apt-get install xserver-xgl
```

and change the session during login to xclient
then try to enable the effects again

---

