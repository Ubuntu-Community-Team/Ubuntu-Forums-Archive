---
title: "clock no longer on menu bar"
date: 2015-03-06
forum: Desktop Environments
---

### Post by parminides on 2015-03-06
I've been running Ubuntu 14.04.2 for awhile. One day my date/clock no longer appeared on the menu bar. In the Time & Date settings, "Show a clock in the menu bar" is still checked. The process appears to be running, i.e.,

```

$ ps -e | grep datet   
 3959 ?        00:00:00 indicator-datet

```

I've tried various fixes.

Attempt 1:

```

sudo apt-get install indicator-datetime
sudo dpkg-reconfigure --frontend noninteractive tzdata
sudo killall unity-panel-service

```

Attempt 2:

```

sudo restart lightdm

```

Attempt 3:

```

setsid unity

```

Attempt 4:

```

dconf write /com/canonical/indicator/datetime/show-clock true

```

Attempt 5:

```

sudo apt-get remove indicator-datetime
sudo apt-get install indicator-datetime

```

Nothing has restored the clock. Any ideas?

---

### Post by jhon_quintero on 2015-03-16
> **parminides said:**
> I've been running Ubuntu 14.04.2 for awhile. One day my date/clock no longer appeared on the menu bar. In the Time & Date settings, "Show a clock in the menu bar" is still checked. The process appears to be running, i.e.,

```

$ ps -e | grep datet   
 3959 ?        00:00:00 indicator-datet

```

I've tried various fixes.

Attempt 1:

```

sudo apt-get install indicator-datetime
sudo dpkg-reconfigure --frontend noninteractive tzdata
sudo killall unity-panel-service

```

Attempt 2:

```

sudo restart lightdm

```

Attempt 3:

```

setsid unity

```

Attempt 4:

```

dconf write /com/canonical/indicator/datetime/show-clock true

```

Attempt 5:

```

sudo apt-get remove indicator-datetime
sudo apt-get install indicator-datetime

```

Nothing has restored the clock. Any ideas?


I killed this process and clock went back to menu bar
/usr/lib/x86_64-linux-gnu/indicator-datetime/indicator-datetime-service


dunno if I have to do this on every reboot, tho

---

### Post by parminides on 2015-03-17
That doesn't work for me. A new indicator-datetime-service process is started immediately after I kill the old one, but still no clock.

---

