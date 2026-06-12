---
title: "Clock showing the wrong time &amp; I cannot set the system time"
date: 2009-03-09
forum: General Help
---

### Post by adam_ski on 2009-03-09
Hopefully this is posted in the right place...

I recently upgraded from 8.04 to 8.10. Since then the time displayed by the clock is a hour fast. I can adjust this manually, but when I reboot it is again a hour fast. On top of that, when I try to edit the system time by right clicking on the clock > Adjust time and date > Set system time I get an error that says ```
**Failed to set the system time**
/sbin/hwclock returned 256
``` I don't know if this is one issue or two separate problems, but any solutions would be gratefully received. 

Thank you.

---

### Post by stumbleUpon on 2009-03-09
Go to system > administration > time and date > unlock using your password, and set the time from there.

---

### Post by adam_ski on 2009-03-09
Ah ha! Thank you, it's now sorted.

---

### Post by bernardfrancois on 2009-05-22
I have the same issue in 9.04.
The bug still remains, but the work-around did the trick. Thanks!

The bug has already been reported, so I hope it will soon be fixed:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/207902?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/207902?comments=all)

---

### Post by Albertint on 2009-06-02
Heh, same problem here, and I too am using 9.04. Though I'm in xfce, so the problem is seemingly more elusive. Or am I going about this all wrong?

---

