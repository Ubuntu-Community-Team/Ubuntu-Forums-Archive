---
title: "Indicator Applet Weirdness (Can't Log Out)"
date: 2010-07-06
forum: Desktop Environments
---

### Post by Lucky. on 2010-07-06
I've noticed in 10.04 that the indicator applet (the power button in the upper right) sometimes disappears and is replaced with my user name.  So what should be this:

[IMG]http://www.ericforyan.com/extra/good.png[/IMG]

Ends up looking like this:

[IMG]http://www.ericforyan.com/extra/lol.png[/IMG]

Clicking the name is ineffective - I can't log out normally...I can add a different applet to log out or turn off the machine, or use the command prompt of course, but that's a little unorthodox.

Anybody else have this problem and find a solution?

---

### Post by nilarimogard on 2010-07-06
Something which will temporarily fix it:

```
killall gnome-panel
```

---

