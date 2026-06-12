---
title: "which processes can I kill to free memory and increase speed?"
date: 2013-07-17
forum: Desktop Environments
---

### Post by webdesigncompanyla on 2013-07-17
Seems like my 12.10 installation has a lot of uneccessary processes.  Which ones can I get rid of without breaking things?

---

### Post by theDaveTheRave on 2013-07-18
webdesigncompanyla,

Looking at your list, probably none of them! they are mostly related to the running unity, and desktop environment. Kill any one of these and you will likely break your dekstop!

A Better test would be to boot to command line then, you run the following
```

top > ~/currentProccesses.txt

```

this will put a copy of the the top's output into a file called currentProccesses.txt in your home folder, you can then log into your desktop and compare this to your output above, and you will see what is the stuff that you are running that is likely 'dekstop dependent'.

After that you will want to get various other desktop environments, and compare thier process list with the other 2 untill you find one that has the memory footprint and functionality that you desire.

David

---

### Post by buzzingrobot on 2013-07-18
A good many of these processes spend most of their time idling about until something happens to wake them up, so their impact on system speed is nil.

If you don't know what a process does, leave it alone. Safer that way.

If you *know* you don't need something, you can disable it.  Doing one at a time is the safer way because one process may depend on another being alive and well.

---

### Post by snowpine on 2013-07-18
It is meaningless to discuss performance without knowing your hardware specs. Kindly enlighten us. :) 
System tools such as 'top' and System Monitor can be very useful in diagnosing performance issues.

---

### Post by dino99 on 2013-07-18
System Tools --> Startup Applications : uncheck what you does not need

---

