---
title: "computer freezes on 12.04"
date: 2012-12-08
forum: Desktop Environments
---

### Post by pmcclure07 on 2012-12-08
I installed 12.04 in September. In the last few weeks my computer has been freezing on a daily basis. I lose mouse, keyboard, can't cntr-alt-F1 - have to hard stop. 
Some google searches showed that many others are experiencing this. Some say its a video driver problem, others say it's not - others say a kernel upgrade (to 3.3.6) is necessary, others say that doesn't fix the problem.
I came to the Ubuntu forum to look for more info - but could not find anything...

Please point me to where i can get more info and a possible solution for this problem.

I am using ubuntu 12.04 on 64 bit Dell inspiron laptop.
Intel® Core™ i7-3612QM CPU @ 2.10GHz × 8 
Ivy Bridge Graphics Controller
driver=i915 latency=0
3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09

Thanks,

---

### Post by BertN45 on 2012-12-09
I have to disappoint you. I have the same i915 driver on my system see my signature and I think it is a driver problem. I am also sure it has to do with parallel processing. I have one CPU, but I can use hyper-threading and in this way the CPUs behaves as two CPU from a software point of view. If I switch off hyper-threading the system works fine, if I switch it on the screen freezes, but I still can use CTR+ALT+F2. In my case it always happens, when I open the Dash, but only if there are other windows open below the Dash.

You have much more parallel processing with the i7 CPU, so probably you have a bigger chance to run into that problem. I am also using 12.10 ad 13.04 and they are using the kernel versions 3.5 and 3.7, but I have the feeling that the optimization of the driver for gaming did make the problem worse.

I tried to file a bug-report, but that one has been rejected because of not enough information, but that was again because the reporting tool in 13.04 was broken due to the GTK upgrade.

I am afraid the only solution is to file a bug-report, but you need a second computer for that and ssh into the frozen computer.
See: [https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Reporting_GPU_lockup_Bugs](https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Reporting_GPU_lockup_Bugs)

---

