---
title: "can't get temperature readings off Dell Inspiron 1100"
date: 2010-01-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bikerbomber on 2010-01-19
Hey all,

     I have Xubuntu 9.10 (Correct forum?) installed on my Dell Inspiron 1100 and want to have a temperature monitor and fan control to control any possible heating issues, but for the life of me I cannot get lm-sensors to detect or locate the thermal sensors. I have the A32 bios but don't trust it for good thermal control. Any help or advice would be great. I have down loaded i8K utils as a package but cannot locate them in linux, and grell fan control won't work without the sensors loaded. Thanks yall.

---

### Post by bikerbomber on 2010-01-20
I'm guessing I need to cut and paste the lm-sensors output messages or really is there somewhere I can get help with this? I am leaving the country to the Philippines on Friday and I need this fixed before then, I hope. Can anyone help? Thanks!!

---

### Post by bobcollard on 2010-01-20
> **bikerbomber said:**
> I'm guessing I need to cut and paste the lm-sensors output messages or really is there somewhere I can get help with this? I am leaving the country to the Philippines on Friday and I need this fixed before then, I hope. Can anyone help? Thanks!!
Check Synaptic Package Manager, you are looking for Xfce4-sensors-plugin.   In Search just type "xfce" (without quotes) and it will get you there.  Then you can use it in your Panel.

---

### Post by bikerbomber on 2010-01-22
Thank you much! I have the readings but cannot seem to find a way to control the fans. I'll keep looking, thanks again!

---

### Post by Onesimus on 2010-01-22
> **bikerbomber said:**
> Thank you much! I have the readings but cannot seem to find a way to control the fans. I'll keep looking, thanks again!

Have you tried installing:

gkrellm
gkrellm-i8k
i8kutils

If you search for gkrellm in the Dell Support Section you will find many threads.

---

