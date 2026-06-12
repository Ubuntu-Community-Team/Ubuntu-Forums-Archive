---
title: "Unity: Screen brightness resets to minimum after reboot"
date: 2011-11-10
forum: Desktop Environments
---

### Post by Forever Delayed on 2011-11-10
I'm having a problem with Unity in Oneiric. Everytime I boot up, the screen brightness is set to the lowest setting. I reset it to the maximum every time, but when I reboot it's back to the lowest setting again. How can I change this so my brightness settings persist?

---

### Post by parminides on 2012-04-24
I found a solution that works for me:

```

sudo gedit /etc/rc.local

```

Add the line

```

setpci -s 00:02.0 F4.B=00

```
    
Above 

```

exit 0

```

---

### Post by parminides on 2012-05-04
Actually, the above solution wasn't a total fix for me. The screen still went dim sporadically.

For a variety of reasons, I eventually reinstalled 12.04 Precise Pangolin from scratch. I still had the same  brightness problem but found a workaround ([http://ubuntuforums.org/showthread.php?t=1971708](http://ubuntuforums.org/showthread.php?t=1971708)). If your brightness slider is backwards, my solution will probably work for you.

---

