---
title: "upgrade to 10.4, after reboot got errors"
date: 2010-09-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ready2DropWin on 2010-09-11
Hi everyone, 

I installed 9.10 on my dell latitude d500, then I upgraded to 10.4 or 10.10 not sure which. But anyhow, I got two errors after reboot, one not a suitable mode found, and two unknown terminal. I found a form on how to change the grub file in etc to fix this, but I can't seem to figure out how to change the read only permissions. Please help.

Thanks again

---

### Post by Ready2DropWin on 2010-09-11
I found that I could hold down shift at startup to get the grub menu, then I pressed e. I then add the i915.modeset=1 to the string, and it booted up just fine. But when I did a restart I still get the same errors. Does it not change in the grub file for the next reboot?

---

### Post by Ready2DropWin on 2010-09-11
I got it now. I changed the quite splash to i915.modeset=1 then I had to run sudo update-grub fix my grub file. Still shows the errors, but it loads the login screen, so at least I can do login now.:p

---

