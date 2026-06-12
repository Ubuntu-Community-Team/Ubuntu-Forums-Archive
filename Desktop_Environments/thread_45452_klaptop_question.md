---
title: "klaptop question"
date: 2005-06-30
forum: Desktop Environments
---

### Post by holr on 2005-06-30
Hi y´all...

Have been using klaptop for a while now under kubuntu and rather like it to keep the speed of my cpu down. just a quick question, what is the difference between the ¨performance profile¨ and ¨cpu throttoling¨ modes?

Dont they both slow down the cpu speed? If indeedy so, why are they both present? I am curious as to the different functions they perform ;-)

cheers!

holr

---

### Post by PhilippWollermann on 2005-06-30
Hi,

the "performance profiles" are real cpu throttling governors (as they're called in the linux kernel). They adjust the clock speed of your CPU based on the system load. There are actually five governors (maybe not all exist, depending on your kernel):

performance: Always maximum clock speed, for best performance.
powersave: Always minimum clock speed, to save power.
ondemand: Adjust the clock speed based on system load, immediately go to 100% clock speed, if system load jumps up.
conservative: Adjust the clock speed based on system load, but increase it more slowly than the "ondemand" governor. This is best for conserving power, while providing a good performance. The Kernel Documentation says, that it's also the best one for an AMD64 system, because the transition latency between minimum and maximum clock speed is very long and thus the "ondemand" governor can't work very good.
userspace: This one is rather special.. it allows a userspace program to control the clock speed. Well.. I don't see any reason, why it should be better than the in-kernel ones, so I don't use it.

Even if one doesn't own a laptop, power-saving can be useful to decrease heat and noise. :-)

CPU throttling is a rather "dumb" way of conserving power: It simply restricts the CPU to do less work, but it won't decrease the clock speed or something like that. As such, it really can get the system performance down, while not actually providing that much power saving.

I hope that helps you. :-)

Philipp

---

### Post by holr on 2005-07-01
[QUOTE=PhilippWollermann]Hi,

the "performance profiles" are real cpu throttling governors (as they're called in the linux kernel). They adjust the clock speed of your CPU based on the system load. There are actually five governors (maybe not all exist, depending on your kernel):

performance: Always maximum clock speed, for best performance.
powersave: Always minimum clock speed, to save power.
ondemand: Adjust the clock speed based on system load, immediately go to 100% clock speed, if system load jumps up.
conservative: Adjust the clock speed based on system load, but increase it more slowly than the "ondemand" governor. This is best for conserving power, while providing a good performance. The Kernel Documentation says, that it's also the best one for an AMD64 system, because the transition latency between minimum and maximum clock speed is very long and thus the "ondemand" governor can't work very good.
userspace: This one is rather special.. it allows a userspace program to control the clock speed. Well.. I don't see any reason, why it should be better than the in-kernel ones, so I don't use it.

Even if one doesn't own a laptop, power-saving can be useful to decrease heat and noise. :-)

CPU throttling is a rather "dumb" way of conserving power: It simply restricts the CPU to do less work, but it won't decrease the clock speed or something like that. As such, it really can get the system performance down, while not actually providing that much power saving.

I hope that helps you. :-)

Philipp[/QUOTE]
 Thanks phillipp, that was exactly what I was after! Do you know if its possible to customise the governors? Is there a .conf or something hiding about the place?

---

