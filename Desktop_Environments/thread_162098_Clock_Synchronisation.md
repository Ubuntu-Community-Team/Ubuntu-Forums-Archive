---
title: "Clock Synchronisation"
date: 2006-04-18
forum: Desktop Environments
---

### Post by harishg on 2006-04-18
Everytime Ubuntu starts the time is changed.I have set the clock to EST but it changes by 3-4 hours during startup.Also during startup I keep getting the message fail to connect to the timeserver of ubuntu or something.

-H

---

### Post by jazzmuzik on 2006-04-18
Since you cannot connect to the timeserver Ubuntu may be setting your clock to Greenich Mean Time, which is the universal time standard. And in EST that will be 4-5 hours difference depending whether Daylight Savings Time is in effect.

If you connect by analog modem then you wouldn't be able connect to the timeserver during bootup until you actually go online later. If that's the case you may need to go into System, Administration, Time & Date and play with the options. Perhaps the "Periodically syncronize clock..." would be helpful if that is the case, but I'm guessing.

Another thought is you can set your time/date in the BIOS during boot up (before Ubuntu loads at all). On most systems you reboot and then press the Del key repeatedly until you get the BIOS menu.

---

