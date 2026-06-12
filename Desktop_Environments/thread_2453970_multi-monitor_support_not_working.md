---
title: "multi-monitor support not working"
date: 2020-11-20
forum: Desktop Environments
---

### Post by yanivbyu on 2020-11-20
Hi, I've recently installed ubuntu on my main machine that has 2 differently oriented displays.
when I went to the setting page to change the rotation of 1 of them the screen blacked out and than ubuntu just disabled my second monitor altogether.
I'm running ubuntu 20.4 btw.
thanks for any help!

---

### Post by CelticWarrior on 2020-11-20
Welcome.

Graphics card/chip?

---

### Post by yanivbyu on 2020-11-20
GTX 1070 gigabyte

---

### Post by CelticWarrior on 2020-11-20
That requires proprietary drivers (Nvidia 450.xx).

Are those installed?

---

### Post by yanivbyu on 2020-11-20
are they supposed to be pre installed or do i need to install them my self?
how do i check if they are installed?

---

### Post by yanivbyu on 2020-11-20
i found out how to check!
NVIDIA-SMI 450.80.02    Driver Version: 450.80.02    CUDA Version: 11.0
i do have the 450.xx.xx drivers installed.
I found out i can edit posts -
another symptom i forgot to mention is that when i changes to a single screen and disables my other 1 it extends the display in a weird way, it makes it so the screen is longer than what actually fits on my display thus making me have to move the mouse the the sides to make the visable portion change.
I hope I managed to relay what I'm seeing as English is not my first language!

---

### Post by yanivbyu on 2020-11-20
Happy to announce that a driver update did in-fact fix the problem.
thanks a lot for the quick help @[**[COLOR=#000000]CelticWarrior[/COLOR]**]("https://ubuntuforums.org/member.php?u=1826209")

---

### Post by sergiuhlihor on 2020-11-27
Which driver version you have? Have you installed something else or changed any settings ? I have similar issues for years with both Ubuntu 18.04 and now 20.04 and could not get it fixed (graphics card GTX 960) .

---

