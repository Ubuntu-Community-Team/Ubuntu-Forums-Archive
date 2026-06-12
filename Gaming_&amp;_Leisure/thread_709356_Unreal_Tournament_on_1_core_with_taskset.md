---
title: "Unreal Tournament on 1 core with taskset"
date: 2008-02-27
forum: Gaming &amp; Leisure
---

### Post by hardsteel on 2008-02-27
Hi,
I am trying to run UT on my Ubuntu 7.10 32bit, but it doesn't run properly due to 2 cores. In windows i just set affinity to 1 core and it works perfectly, but i cannot manage to do it in linux. I read some topics and tried out some tool called 'taskset' but I couldn't get it working. I go to UT/System directory in terminal and enter this command I think should launch UT on 1 core:
taskset -c 1 ut-bin
and this is what i get:
execvp: No such file or directory
failed to execute ut-bin

Can anyone tell me what I'm doing wrong or recommend an alternative? 
Thanks,
h.

---

### Post by hardsteel on 2008-02-27
Ok I got it running by using the cmd
taskset -c 1 ./ut-bin
but the UT still runs at the double speed.. any suggestions?
h.

---

### Post by hardsteel on 2008-03-02
All my problems solved, installed WinXP  :roll:

---

