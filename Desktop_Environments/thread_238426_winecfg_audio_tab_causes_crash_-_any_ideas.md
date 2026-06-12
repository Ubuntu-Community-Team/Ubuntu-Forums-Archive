---
title: "winecfg audio tab causes crash - any ideas?"
date: 2006-08-17
forum: Desktop Environments
---

### Post by dpaint4 on 2006-08-17
I'm having a bit of trouble with Wine on my latest install of 6.06. I'm running wine 0.9.9-0ubuntu2.

I need to configure the sound via the "Audio" tab in winecfg - something I've done in the past without a hitch on this same version of Ubuntu.

Now when I open winecfg and click on the "Audio" tab, the program instantly crashes and generates this message in the terminal:

```
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file o r directory
Link points to "/tmp/ksocket-dpaint4"
can't create mcop directory
```

What do you think is happening and what do you think I should do to fix it?

---

### Post by waldschm on 2006-08-17
Check out this thread on the topic:

[http://www.ubuntuforums.org/showthread.php?t=210684](http://www.ubuntuforums.org/showthread.php?t=210684)

---

### Post by dpaint4 on 2006-08-17
Thanks a lot; I thought my issue was exotic and probably my own fault. I should have searched the forums anyway. I appreciate the guidance.

---

### Post by waldschm on 2006-08-17
Oh I just noticed something else, did you mean Wine 0.9.19? If not your wine version is a bit dated. This repository has the newest version for dapper:
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

