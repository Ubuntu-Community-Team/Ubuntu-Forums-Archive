---
title: "XFCE not loading after installing Bumblebee"
date: 2014-10-03
forum: Desktop Environments
---

### Post by tired-triclops on 2014-10-03
I'm on a mid-2010 Macbook Pro and installed Xubuntu 14.04 in a dual boot configuration. I installed Bumblebee to enable switching between integrated graphics and the discrete nvidia card installed. However, after installing and rebooting, X does not automatically load (though that can be manually started by opening the tty with Ctrl+Alt+F1 or F2 and running startx). After manually starting X, XFCE does not load/start.

How would I go about getting XFCE (and X) to start automatically at boot/login?

---

### Post by Habitual on 2014-10-08
How was bumblebee installed exactly?

Can you check and report the value of 
"env DEFAULT_RUNLEVEL" in /etc/init/rc-sysinit.conf please using

```
grep "env DEFAULT_RUNLEVEL" /etc/init/rc-sysinit.conf
```


Thank you.

---

