---
title: "Ubuntu slows down to a crawl after running overnight."
date: 2006-08-29
forum: Desktop Environments
---

### Post by UrbanSage on 2006-08-29
I have tried installing Ubuntu 6.06 on two different PC's and with both I experience a slowdown after leaving them running overnight. When I come to work the next day I will be able to move the mouse around but when I click anything the computer slows down and not much happens. Looking at the time I can see that it stopped or slowed down some time the evening before. My only means of rebooting which fixes this is to ssh to the box and then reboot from there. The sshd is slow to respond as well. 

This has happened on a number of systems now. And I have had it happen on two systems very recently I use at work.

Has anyone else experienced this?

---

### Post by kwalo on 2006-08-29
My guess is - you are running a program, which leaks. Have you checked your memory? Is your swap full?

---

### Post by UrbanSage on 2006-08-29
This happens on fresh installs I have done absolutely nothing to.

My second to last system had apache running. The latest system I built for my home. Just to see if it would act the same I only finished the install and then I left the system alone. The next day it has slowed to a crawl. This is different hardware.

From what I can tell, memory and swap is hardly used at all.

---

### Post by Omnios on 2006-08-29
From what I have read over the year or so that I have been using Ubuntu is that leaving it on all the time causes huge caches im memory which slowes Ubuntu down. It may be possible to eleviate this by using ctrl-alt-Backspace to restart xserver.

---

### Post by UrbanSage on 2006-08-29
What good is a Linux distro I can't leave on? :(

Do you happen to know a link or two to discussions about this?

---

### Post by UrbanSage on 2006-08-29
Can it really be that this is not a more common issue? With me experiencing it on multiple freshly installed systems I would think its a fairly common problem.

---

### Post by Ramses de Norre on 2006-08-29
My system is as responsive as before when it's been on more then a day. 
And I never heard of this issue before so I'm afraid it's not that common..

---

### Post by doobit on 2006-08-29
> **UrbanSage said:**
> Can it really be that this is not a more common issue? With me experiencing it on multiple freshly installed systems I would think its a fairly common problem.

Open a terminal and run top to see what's eating your memory.

---

### Post by Omnios on 2006-08-29
Well it could be a memory leak or possibly caching as for caching windows  is even worse.

---

### Post by UrbanSage on 2006-09-07
The system has been reinstalled on new hardware with new downloaded ISO and same thing is going on. This time I even let it do the partitioning for me.

I have top running on terminal 1 showing that I have plenty of unused RAM and my swap is not in use. No cpu usage either.

---

### Post by jacket on 2006-10-24
I'm having this same issue...anyone else find anything out?

Any replies appreciated!

Thanks,

Jacket

---

