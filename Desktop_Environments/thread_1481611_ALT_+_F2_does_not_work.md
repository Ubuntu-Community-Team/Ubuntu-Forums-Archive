---
title: "ALT + F2 does not work"
date: 2010-05-12
forum: Desktop Environments
---

### Post by samsonite2010 on 2010-05-12
This is more of a tip that may help some people as I found a closed thread on this, but it did not have an actual solution (just a workaround).

Although I had this problem on Xubuntu and it turns out that it was because I had killed xfce4-settings-helper, I think there may be a similar fix for Gnome and KDE.

So to get ALT + F2 working again, just run this in terminal:

```
xfce4-settings-helper
```

I guess there are other versions of this for Gnome and KDE, but I am not using those at the moment.  Gnome maybe something like gnome-settings-daemon-helper if someone wants to try!

Thanks,
S

---

