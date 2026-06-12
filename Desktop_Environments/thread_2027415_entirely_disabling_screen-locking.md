---
title: "entirely disabling screen-locking"
date: 2012-07-16
forum: Desktop Environments
---

### Post by N-t-F on 2012-07-16
Hello,

this question is related to [http://ubuntuforums.org/showthread.php?t=2024170](http://ubuntuforums.org/showthread.php?t=2024170), but trying to narrow things a bit.

I would like to know if there is a way to completely disable screen-locking on Ubuntu 12.04 (even in case of sleep/suspend/hibernate, which I would happily disable too, by the way). I'm specifically thinking about xfce or gnome-classic, but I may be interested in other desktop environments, if they can save my day. A way to remove it for all environments at once would be the perfect shot, actually. :mrgreen:

Thank you very much. :)

---

### Post by lptr on 2012-07-17
Did you try something like this?

[http://jacob.steelsmith.org/category/section/ubuntu-kiosk-edition](http://jacob.steelsmith.org/category/section/ubuntu-kiosk-edition)

Maybe him found a solution for your problem?

---

### Post by N-t-F on 2012-07-18
Hi, and thanks for the tip. His solution is apparently based on Lucid though, where I had what I wanted already working.

But I have found another way, related to the solution proposed in my linked topic. What seems to work so far (in Xfce) is to change ownership to rootlocal.admins (rootlocal being my local sudoer account and admins being the group for the administrators stored in the LDAP directory) and rights to 770 for the following files :

```
/usr/bin/xflock4
/usr/bin/gnome-screensaver
/usr/bin/xscreensaver
```

The system where I've tried this has already been tortured for the past week in the hope of making it unlockable, so I'm not yet entirely sure whether these rights changes alone are enough or if they just complete previous tweaks. I'll post an update in the latter case.

---

