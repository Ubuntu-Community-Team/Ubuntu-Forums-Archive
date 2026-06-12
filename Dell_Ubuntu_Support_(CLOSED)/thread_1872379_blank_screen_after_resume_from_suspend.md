---
title: "blank screen after resume from suspend"
date: 2011-10-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by roberto03 on 2011-10-30
I have freshly installed 11.10 on my Dell D600.
I suspend the laptop but when i try to resume, the screen stays blank.
No tty available. 
Nothing. Just the fan on and the totally blank screen.

The same problem occurs with hibernate.

Is it still a bug ?
I have googled a lot, but there seems to be no workaround yet.

Thank you for any suggestions.

---

### Post by NikoC on 2011-12-17
No solution, but same problem,
running Kubuntu 11.10 64-bit on a dell e6510 and problem occurred since laste kernel update(3.0.0-15 kernel).

---

### Post by 2F4U on 2011-12-17
What are the hardware specs, what graphics driver are you using? Did you look into the log files, in particular
- /var/log/pm-suspend.log
- /var/log/pm-powersave.log

---

