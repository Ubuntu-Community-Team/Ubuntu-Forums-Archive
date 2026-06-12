---
title: "Timed Internet Solution?"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Johnsie on 2006-07-24
Hi, I'm not sure if this is the right board to post on but here goes:

We have a 16 year old foriegn visitor staying at our house at the moment. All he does all day is uses the computer and when you ask him to do anything he just says no and keeps on using the computer. Even when you ask him to get off the computer so you can do work he says no!

Short of kicking him out of the house for rudeness, are there any other solutions which would stop him from getting on the Internet at certain times?

The computer is behind a router but  router does not cover ttimmed banning. Is there a way to do it in Linux? Preferably automatically.

---

### Post by Paerez on 2006-07-24
Check out cron jobs. They let you run commands at specific times. Generally they are used for server administration (like run an upgrade at 3am or something) but you could just put in the shell command to turn off the internet devices, then make sure his user account does not have enough authority to bring the network back up. Then later, you could run the command to bring up the device.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

the command to turn on device eth0 is:
ifconfig eth0 up

and turn off:
ifconfig eth0 down

if its a wireless card it may be eth1.

---

### Post by Johnsie on 2006-07-24
Thanks... I've been dying for a chance to use cron jobs for something  :-)

---

### Post by Paerez on 2006-07-24
give the little guy a digital kick in the pants for me. thats just rude. Good luck with cron, I have never used cron jobs, so I won't be of much help beyond being a second source of common sense.

---

