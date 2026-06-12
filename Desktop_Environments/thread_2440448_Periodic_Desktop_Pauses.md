---
title: "Periodic Desktop Pauses"
date: 2020-04-10
forum: Desktop Environments
---

### Post by rsteinmetz70112 on 2020-04-10
Not that I working at home using a Linux 18.04 Desktop for work I've noticed an issue. Every once in a while the desktop seems to freeze, that is nothing much will respond. If I have the System Monitor running it keeps reporting but shows no unusual activity 0-4% usage of 4 cpus, less than half of the memory used, little or no swap, little or no network activity. After several minutes it tends to start back up.  The problems seem related to email (Thunderbird) and Browser (Firefox and Chrome) although it affects LibreOffice but not open terminal windows.

I'm guessing it may be due to the video driver. I'm using a Radeon HD 4250 with the raedon driver.

Any idea how to pin it down and what to do about it?

---

### Post by mikewhatever on 2020-04-12
Can you add the output of <free -m> to the question?

---

### Post by rsteinmetz70112 on 2020-04-14
Here it is:

```
$ free -m
              total        used        free      shared  buff/cache   available
Mem:           3692        1351        1308          83        1031        2009
Swap:         16377         802       15574
```

Since I almost always have Firefox and Thunderbird open I'm beginning to wonder if it isn't some javascript, but I don't see it consuming a lot of resources.

---

