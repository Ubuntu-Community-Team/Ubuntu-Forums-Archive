---
title: "Do I need to *DO* anything to enable SMP in linux-686"
date: 2006-04-27
forum: Desktop Environments
---

### Post by JamesNorris on 2006-04-27
I installed Linux-686-smp from apt, but I'm not sure if it's working, back when I used windows, I would have Folding@home always using 50% CPU (100% of my HT enabled P4 logical 2nd CPU) now it still seems to be using 90% all the time.

How do I check that I have SMP working?

Do I need to do anything else, now I've installed linux-686-smp from apt?

---

### Post by khightower on 2006-04-27
The easy way is to go to System>Administrator>System Monitor

When you click on the resources tab you will CPU History. If SMP is working you will see CPU1 and CPU2 working.

---

### Post by khightower on 2006-04-27
[QUOTE=JamesNorris]I installed Linux-686-smp from apt, but I'm not sure if it's working, back when I used windows, I would have Folding@home always using 50% CPU (100% of my HT enabled P4 logical 2nd CPU) now it still seems to be using 90% all the time.

How do I check that I have SMP working?

Do I need to do anything else, now I've installed linux-686-smp from apt?[/QUOTE]

I have a Dual Core PentiumD and after updating the Linux Kernel to 686-smp. Both CPU's showed up in the System monitor under the Resources tap.

I have a screen shot below

---

