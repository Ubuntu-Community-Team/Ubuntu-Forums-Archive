---
title: "Computer Locks up when I try to adjust time, and is fast"
date: 2006-08-29
forum: Desktop Environments
---

### Post by statictonic on 2006-08-29
The clock on my computer seems to run about 10-15 minutes fast after 24 hours, not only that but it also locks up if I try to change the time in ubuntu, I have to use the logout keyboard shortcut to unlock it, when I log back in it is changed though.

So two things, what is causing my time to go faster than it should and more importantly, why does it lock up everytime i change it even when i'm changing it from the console.

(my temp fix was going to have a cron job to sync the clock every 30 minutes with a time server, but since it locks up when updating the time that won't work...)

Any help would be awesome!

-Mark

---

### Post by mcduck on 2006-08-29
The most common reason for clock running too fast in computers is that CMOS battery is running out of power and should be replaced with a new one. It's the flat battery somewhere arounf your motherboards lower right corner.

That wouldn't explain your lockups when adjusting time though.

---

### Post by statictonic on 2006-08-29
My CMOS battery is fine I've replaced it several times, I guess fixing the lock up when changing my time would fix the problem fully, because i could set a cron job to update time every 30 minutes or hour then.  If anyone has any ideas let me know...

---

### Post by hajk on 2006-09-01
There are several kernel boot options that you can experiment with, e.g.
"clock=pit" OR "noapictimer".

---

