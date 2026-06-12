---
title: "Remote machine should be third monitor in xrandr"
date: 2011-01-10
forum: Desktop Environments
---

### Post by dlublink on 2011-01-10
Hello,

I ran the following commands on my ubuntu desktop :

xrandr --output VGA-0 --mode 1680x1050
xrandr --output VGA-1 --mode 1680x1050
xrandr --output VGA-1 --left-of VGA-0

This gives me dual head. I have a second machine on the same 100mbps network that is also running Ubuntu. I want to run X on that machine and have it's X session as a monitor in xrandr, so I would add something like this :

xrandr --output REMOTE-1 --right-of VGA-1

Is this possible? Any ideas of where to start looking ?

I am using Ubuntu 10.04 LTS.

Thanks,

David

---

### Post by dlublink on 2011-03-21
So, has nobody answered because it can't be done or because I did not include enough info?

Thanks,

David

---

