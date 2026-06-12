---
title: "Have to Reset Time Everytime I Boot"
date: 2009-01-08
forum: Desktop Environments
---

### Post by corsairgt on 2009-01-08
My Ubuntu 8.10 was installed on an USB flash drive. I configured the OS as follows:

System->Time and Date:

         Time zone: Asia/Hong_Kong
         Configuration: Keep synchronized with Internet servers
         Time servers: clock.cuhk.edu.hk (Hong Kong, China)

However, the time zone is not saved and reset to Africa/Accra every time. Does anyone have a clue?

---

### Post by badea on 2009-01-08
Hi! I have almost the same problem.... I've got a dual-boot system (XP/Ubuntu) and in the beginning the problem was that each time i booted into XP (after Ubuntu) the clock in XP was 2 hours earlier normal time. I kind of fixed this by setting UTC=NO in /etc/default/rcS  
Now the clock in XP is ok, but the Ubuntu clock is 2 hrs earlier... 
Can someone give me a hint what to do?
Thanks!

---

