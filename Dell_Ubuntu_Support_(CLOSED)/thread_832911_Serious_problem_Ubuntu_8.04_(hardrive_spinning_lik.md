---
title: "Serious problem Ubuntu 8.04 (hardrive spinning like mad)"
date: 2008-06-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by keryonic on 2008-06-18
I have installed Ubuntu 8.04 on a Vostro 1310 about 1 month ago. After many difficulties and fine tuning, I was about satisfied (except mic not working).

BUT now I am in serious trouble. Yesterday and today (and another couple of times in the past), my disk drive started spinning and slowed down my whole system. There is no way to stop it, even logging out it keeps spinning.

The hard disk and the system seem to be very busy at doing something but I don't know what. The system becomes unstable and very very slow. Yesterday, after 30 minutes patience I managed to log out but since it didn't solve the problem, I had to power off. I also managed to enter "System monitor" but I didn't see any strange process in progress. (By the way, is there an easy way to enter "System Monitor"? In Windows XP Ctrl-Alt-Del brings you easily there even during most unstable processes).

My configuration is a very standard dual boot system. My hard drive is partitioned in Vista, Recovery (Vista), Ubuntu, /home, and Swap.

Please help, if this failure reproduced, I will have to go back to Windows.

---

### Post by keryonic on 2008-06-18
The problem was Pidgin!!! It was eating up all my RAM (96% of 2GB). I killed it, substitute it with Emesene and now it works smoothly.

---

