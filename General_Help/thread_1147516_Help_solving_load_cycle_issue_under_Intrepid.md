---
title: "Help solving load cycle issue under Intrepid"
date: 2009-05-03
forum: General Help
---

### Post by thealmightyone on 2009-05-03
A week or so after installing eeebuntu on my eeepc (no configurations changed), read about the load cycle issue, and decided to look at my count, which was 1000. Since then, I have attempted to solve the problem.

One of the solutions was to turn off hard drive management (setting it to 254). I have tried values between 190 and 252, all of them result in 30 (give or take 2) load cycles per 15mins of IDLE.

Yesterday, found a thread here, although made last autumn, about reducing how often the kernel writes to the disk, and have tried setting it to write every 60 secs, then 600 secs, neither of which have solved the load cycle issue. Here, I was assuming that the kernel writing was the cause of the issue, but apparently not.

I really would like to reduce the load cycle count from its cause, not just by turning off hard disk management, as that just gets rid of the symptom, but brings in another issue off more heat and reduced battery life. Any ideas?

---

