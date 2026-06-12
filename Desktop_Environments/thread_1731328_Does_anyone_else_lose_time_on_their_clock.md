---
title: "Does anyone else lose time on their clock??"
date: 2011-04-17
forum: Desktop Environments
---

### Post by Amused2Death on 2011-04-17
It's not that important, but my Ubuntu 10.10 desktop loses time over several days. This time around it lost 25 minutes over 40 hours.
Its not the pc as it dual boots with windoze xp and it doesn't lose any time.

Just curious if it happens to anyone else??

---

### Post by K_45 on 2011-04-17
You may need to replace the CMOS battery - are you sure windows isn't losing time?

---

### Post by GregBrannon on 2011-04-17
Agree that your computer's clock may be losing time when it is shut down, so you should check the CMOS battery.  The next symptom will be that your startup settings stored in BIOS may have to be reset if any are other than the default.

XP is probably configured to sync time with one of the internet time sources but you have not configured Ubuntu to do the same thing.

---

### Post by Amused2Death on 2011-04-17
Ok i should have stated that it only happens when the computer is left on for extended periods.

Last time it lost 25 minutes over 40 hours of being on.
If i turn it off and restart all is good.

Its just a curiosity at the moment as i dont rely on it.

---

### Post by thecamelcoder on 2011-04-17
Hey there, the reason that you will be seeing this under ubuntu and not windows is that windows has a regular time sync service. If its enabled that is.

Linux has the same functionalituy but it needs to be set up. Its called ntpd - Network Time Protocol Daemon and can be installed by

```
sudo apt-get install ntp
```

This should keep your time in line, but I agree with the others that the root cause is no doubt your CMOS battery. 

Thanks
[http://www.linux-geek.co.nz](http://www.linux-geek.co.nz)
):P

---

### Post by Amused2Death on 2011-04-22
Installed, and thanks

---

