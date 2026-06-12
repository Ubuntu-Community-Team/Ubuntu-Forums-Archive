---
title: "Hard drive. Who's the master, and who's the slave?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by Jimmey on 2006-09-05
I gave my friend a spare hard drive I had, because the one he had was getting quite full, and he wanted to try Ubuntu.

We opened up his Dell, and there was a single hard drive, connected by a single IDE cable to the motherboard. No room for another hard drive. Which was kind of a bad sign.

So we tried plugging it in, and after a bit of fidgiting, I got Ubuntu installed on the hard drive, with Grub recognizing the fact that Windows was on the other drive, and a line in fstab mounting that drive into /home/windows every boot. We were even reading files from the Windows drive, so it worked all fine and dandy. Until: 

When we tried booting into Windows, Grub said "The selected drive does not exist". Which, I'm assuming is because Windows doesn't like being on the slave drive in a computer ( fdisk -l listed it as being on /dev/hdb ). So, I assumed that if we swapped the drives round on the twin IDE cable we put in, it'd boot straight into Windows, leaving me with the gruesome task of trying to get Grub onto that drive, instead.

But when we swapped the drives and switched the computer on, nothing booted. At all. No Windows, no Ubuntu, nothing. 

Just wondered if I'm doing something wrong. 

Any help's appreciated :-)

Thanks

---

### Post by tminuszero on 2006-09-05
The problem might be the jumpers on the drives. Did you change those in any way?

---

### Post by Jimmey on 2006-09-05
Honestly, I don't know what those are :(

---

### Post by confused57 on 2006-09-05
> **Jimmey said:**
> Honestly, I don't know what those are :(
There should be a diagram on the top of your hard drive where the jumper should be connected(placed) on the back of your hard drive for master, slave, or cable select.  Your dell probably supports cable select, both master and slave can be set to cable select.

Also, you'll need to go into your bios setup(press F2 during startup, you'll see a prompt for it)...find your hard drive settings and make sure hd0 and hd1 are set to "auto" or "enabled", I think it's auto, for bios to recognize your slave drive.  It'll probably just be hd1(slave) drive that you'll need to set to auto.

See this guide for setting Ubuntu as master and Windows as slave:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by Jimmey on 2006-09-05
Thanks for that. My friend says he'll look into it.

Again, thanks :-)

---

