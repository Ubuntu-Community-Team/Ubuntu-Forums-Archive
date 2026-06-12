---
title: "powernow / cpu freq applet / cpuinfo on amd64"
date: 2005-10-14
forum: Desktop Environments
---

### Post by robot on 2005-10-14
Hi all,


I was running powernowd under Hoary successully to throttle my 2.2GHz amd64 when idle (reduce heat). I just upgraded to breezy and have the following issue:

According to /proc/cpuinfo and the cpu frequency scaling applet, the processor runs at 1GHz all the time (which is the minimum frequency), even under high load.

However, if I stop powernowd and run it manually with 

```
powernowd -dvvv
```

I can see it throttling up / down nicely depending on load. So, powernowd itself seems to be working (and all the necessary modules are installed), but neither /proc/cpuinfo or the applet (which might just use /proc/cpuinfo) seem to notice the throttling.

Any ideas?

Cheers!

---

### Post by magnusbb on 2005-10-15
You're right - there is a bug in Breezy which makes the powernowd unusable at startup. But this is easy to fix.

To change this, create a file called /etc/default/powernowd.

Type:

```
sudo gedit /etc/default/powernowd
```

and feed the file with the following:

```
OPTIONS="-q -m 1"
```

Then restart your computer and tell me what you think. I like it.

---

### Post by robot on 2005-10-15
I booted up my box this morning and, for some reason, everything seems to be working quite fine today... weird.

I'll post if things go AWOL again.

---

