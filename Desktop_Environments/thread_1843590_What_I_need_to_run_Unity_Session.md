---
title: "What I need to run Unity Session"
date: 2011-09-13
forum: Desktop Environments
---

### Post by Taltos DCLXVI on 2011-09-13
Hi,

I installed Ubuntu 11.04, but when installation finished, and ubuntu runs for the first time, it appears a legend that says something like this: " Your computer does not have the requierements for Unity", and then a gnome session start.

I have this in my computer:

AMD Dual Core 2600
2 Gb RAM
1 TB Hard Disk
9600 GT Nvidia Card

Do you know what i need to run Unity???

Thanks

---

### Post by MG&amp;TL on 2011-09-13
You need to install the driver for your AMD.

system>administration>hardware drivers.

Should then work.

---

### Post by Taltos DCLXVI on 2011-09-13
ok, if i understand, i have to install drivers for my AMD processor??

---

### Post by Blasphemist on 2011-09-13
Do enable the nvidia driver as MG&TL describes and that should do it I think. There is also a script that ubuntu runs to make the determination if unity 3D can be run.
```
/usr/lib/nux/unity_support_test -p
```
You can run that yourself from the terminal. I got it from this document. [https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

If you still can't run unity, do let us know.

---

### Post by MG&amp;TL on 2011-09-13
On windows, they may have been pre-installed, but linux is free, so it can't do that.

To get the most out of your hardware, you install proprietary drivers.

once in System>administration>hardware drivers>click on the reccommended entry, leave it for a while, and reboot. You should then be able to run Unity.

---

### Post by Blasphemist on 2011-09-13
> **Taltos DCLXVI said:**
> ok, if i understand, i have to install drivers for my AMD processor??

The driver that may need enabled is for the nvidia card.

---

### Post by Taltos DCLXVI on 2011-09-13
Thanks a lot for your quick answers.

I'll try tonight.

---

### Post by Taltos DCLXVI on 2011-09-14
I want to thank you again.

I did what you told me. 

I installed Nvidia Drivers in gnome session, after this i reboot, then Unity worked.


Only one more question, how do i mark this message with [Solved] tag?

;)

Regards,

---

### Post by Blasphemist on 2011-09-14
As the thread creator, you will have the ability to mark it solved under thread tools. [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

