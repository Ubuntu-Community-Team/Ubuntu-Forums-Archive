---
title: "Ubuntu on a Dual Processor Machine"
date: 2006-03-30
forum: Desktop Environments
---

### Post by larry on 2006-03-30
Dear All,
For my job (numerical simulations) I should be given, in a month or so, a dual processor machine (I do not know yet whether it will be a workstation or a PC), but I think it should be able to run linux.
Newbie question: is it difficult to install Ubuntu on such a machine? Is Breezy/Dapper able to recognize and use the the 2 processors out of the box or will I end up doing a lot of manual configuration to set everything up?
It probably makes more sense to ask this question once I have the machine, but I just wanted to have a rough idea of what I should do.
Many thanks

Larry

---

### Post by John.Michael.Kane on 2006-03-30
you would have to install the SMP Kernel after your frist install of ubuntu. since i don't know what the rest of the hardware in the system will be, I can't tell you if you will have any other issues or not.

---

### Post by localzuk on 2006-03-30
Yep - it should work fine. You simply need to install a 'SMP' kernel (these can be downloaded post initial install by using apt-get, aptitude or synaptic.)

---

### Post by art on 2006-03-30
I am using a dual XEON 64 bit machine, and the SMP kernel from synaptic didn't work for me, I think I was getting kernel panic on boot, so I ended up compiling my own kernel, which is very easy. And no need to play with configs a lot.

---

### Post by localzuk on 2006-03-30
You have to choose an SMP kernel specific to your architecture - so if you selected the SMP kernel for EMT64 it may not work. The easiest way would be to try them out and if not, take a look at: [https://wiki.ubuntu.com/KernelHowto](https://wiki.ubuntu.com/KernelHowto) for instructions on how to compile your own in the most efficient manner for Ubuntu.

---

### Post by larry on 2006-03-31
Thanks a lot for the many replies. It is difficult for me to be more specific at this stage (I do not remember the suggested brand of the machine...could it have been a Fujitsu or something like that? 100% sure my spelling is wrong).
Hopefully it should all boil down to selecting a new kernel.
I once tried to compile my own kernel and I screwed my system...I did what nobody thought possible!
Another question: what should I type in a terminal to find out which processors my system can see and use?
Many thanks

Larry

---

