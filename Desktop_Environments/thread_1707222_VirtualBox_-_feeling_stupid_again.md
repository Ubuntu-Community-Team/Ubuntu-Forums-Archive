---
title: "VirtualBox - feeling stupid again"
date: 2011-03-15
forum: Desktop Environments
---

### Post by rpaskudniak on 2011-03-15
Greetings.

I am posting this in the "Desktop Environments" section on the theory that the VirtualBox is indeed a desktop environment.

Bottom lines first - maybe it will make the whole essay below superfluous.

[LIST=1]
[*]Do I need to use the Windows-7 installation disk to install the "guest" OS into this virtual box?  (This is the main question.)  I suspect it is, after the prompts I get trying to run my guest OS for the first time.
[*]Since I have a dual-boot anyway - with Win-7 as the main OS on the machine - is there any way I can configure Virtualbox to use the existing Win-7 installation as a guest OS, without damaging the Windows partitions?
[/LIST]

Now the rest of the story:

I just deleted about 100 lines of torturous details, realizing nobody will want to read through all that.  Please, someone, confirm my suspicion in question 1.  Question 2 is optional - I have a 400GB mounted file system on a huge Seagate drive for my guest "hard drive".

Thanks.

---

### Post by ChipOManiac on 2011-03-15
What is in the ".vdi" file? The Win7 install disk?

---

### Post by mlentink on 2011-03-15
> **rpaskudniak said:**
> 

[LIST=1]
[*]Do I need to use the Windows-7 installation disk to install the "guest" OS into this virtual box?  (This is the main question.)  I suspect it is, after the prompts I get trying to run my guest OS for the first time.
[/LIST]
A virtual machine is just like a real one. So yes, you need to install an operating system. Please remember to set up the cd or iso in VBox before installation> **rpaskudniak said:**
> Since I have a dual-boot anyway - with Win-7 as the main OS on the machine - is there any way I can configure Virtualbox to use the existing Win-7 installation as a guest OS, without damaging the Windows partitions?

Don't know about Win7, but technically this should be possible though highly inadvisable, because yes, you will run a high risk of borking your existing installation. Furthermore, you virtual hardware is completely different from your real hardware, so you will have problems with registration. Microsoft will consider this a second installation where only one is allowed.


Edit: Perhaps you could share what it is you want to achieve?

---

