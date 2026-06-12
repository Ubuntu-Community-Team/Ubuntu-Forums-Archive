---
title: "Messed Up Screen After Restart"
date: 2011-04-29
forum: Desktop Environments
---

### Post by Morgan74 on 2011-04-29
Hi All:
I just installed 11.04 using wubi.  It runs fine for the fist few start / restart cycles, but then the screen goes crazy.  I'm sure it's not the monitor because Win7 boots fine, and it also lets me take screenshots of it (see attached).  I've even done a complete reinstall and had the exact same result.  Anyone ever run into this before.  I'm running an older Inspiron 6000, but it has the best graphics card one could get at the time.
[IMG]http://farm6.static.flickr.com/5268/5669674608_51a9e6260c_o.png[/IMG]

---

### Post by sikander3786 on 2011-04-29
Welcome to the forums :-)

Which graphics card is there exactly and did you install the proprietary drivers?

---

### Post by Morgan74 on 2011-04-29
It's an ATI Mobility Radeon X300.  Nope, I didn't install the driver manually because it seemed to be working fine initially.

{UPDATE}I just restarted from Win7 and now it's working fine? Maybe it is a wubi issue.  I'll still install the driver just to be safe.

---

### Post by sikander3786 on 2011-04-29
> **Morgan74 said:**
> It's an ATI Mobility Radeon X300.  Nope, I didn't install the driver manually because it seemed to be working fine initially.

{UPDATE}I just restarted from Win7 and now it's working fine? Maybe it is a wubi issue.  I'll still install the driver just to be safe.
Yes I think, driver installation might sort the issue.

---

### Post by Morgan74 on 2011-04-29
Now if I can only find the driver.  Benn searching for about an hour.

---

### Post by Morgan74 on 2011-04-29
OK I finally got the driver installed and it seems to be working fine.  It is a "legacy" card and ATI's driver doesn't support 11.04 so I had to run it in compatibility mode using --listphg & --buildphg Ubuntu/8.10   Everything seems to be working great now.

---

### Post by drpjkurian on 2011-04-29
Please mark the thread as solved

---

