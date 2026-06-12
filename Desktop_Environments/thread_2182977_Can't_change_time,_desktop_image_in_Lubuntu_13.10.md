---
title: "Can't change time, desktop image in Lubuntu 13.10"
date: 2013-10-23
forum: Desktop Environments
---

### Post by hJrBzw3 on 2013-10-23
I just performed a fresh install of Lubuntu 13.10 on a laptop (after a long, frustrating battle with Windows 8). Everything works beautifully except that the time and date is synced to the incorrect time zone. (I did the install in GMT -5, now I live in GMT +1). The time in BIOS is correct, however. When I try to change it via the GUI in System Tools >>> Time and Date, everything is grayed out. Hitting "unlock" does not prompt a dialogue box where I can enter my password. Things I've tried to no avail:

1. sudo hwclock -s
2. sudo date --set 

The problem seems to be that the time is synced to GMT -5 instead of GMT +1. Is there a simple CL option I can use that I just am not thinking of in my jet lagged stupor?

Another, less annoying problem (that maybe is related to the same weirdo desktop issue?) is that the desktop image resets itself to the Lubuntu default every time I reboot.

---

### Post by TheFu on 2013-10-23
I set the BIOS clock to UTC, then use the timezone on every OS to control the local dispaly of time.

Open a terminal and run
**sudo tzselect**
Then logout and login.

---

### Post by hJrBzw3 on 2013-10-23
Thanks! That did the trick for the time display. I knew there must have been a CL option I didn't know/wasn't thinking of. =P

---

