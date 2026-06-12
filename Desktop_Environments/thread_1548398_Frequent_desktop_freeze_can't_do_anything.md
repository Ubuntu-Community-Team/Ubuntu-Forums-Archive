---
title: "Frequent desktop freeze: can't do anything"
date: 2010-08-08
forum: Desktop Environments
---

### Post by rocketman768 on 2010-08-08
Hi. I'm running Kubuntu 10.04. I am frequently having complete freezes of the system when running the desktop (maybe every 2-4 hours). It seems random, and when it occurs, I can't even use ctrl-alt-f2 to switch to a console. All activity ceases, and all I can do is a hard reboot. This is bad, because it has screwed up one of my backup disks as I had a backup operation going on yesterday, so this has made me want to get this fixed.

First, I don't think it's the video driver. I was using the non-proprietary driver for nvidia cards until yesterday, then I switched to the proprietary one, and still the same thing.

I used to have some freezing problems related to the ath5k driver (I think) for my wireless card in previous versions. I think I had solved the issue by switching to madwifi. I tried to switch to madwifi yesterday by going to the "hardware drivers" dialog. However, that didn't work for some reason and I'm still using ath5k, only now the option doesn't appear anymore in the dialog :-/

I have checked /var/log/kern.log and Xorg.0.log, but nothing really jumps out at me. Can you help me figure out what is going on please?

---

### Post by clrg on 2010-08-08
The next time it freezes, don't cut the power. Press and hold Alt+SysRq keys, then press R E I S U B one after another (while holding Alt+SysRq). That will take away keyboard control from X11, flush filesystem buffers, unmount filesystems and force a reboot on kernel level. This usually prevents filesystem damage.

---

### Post by rocketman768 on 2010-08-08
> **clrg said:**
> The next time it freezes, don't cut the power. Press and hold Alt+SysRq keys, then press R E I S U B one after another (while holding Alt+SysRq). That will take away keyboard control from X11, flush filesystem buffers, unmount filesystems and force a reboot on kernel level. This usually prevents filesystem damage.

Thanks. My keyboard does not list the SysRq key, but it does have the Print Screen key which is usually the same button. Can I safely assume they are the same? Second, am I going to have to get a 3rd person to press R E I... or should I just use my nose ;)

Alright, assuming I can do that, then I can recover from each freeze. Now, how do I figure out *WHY* it's freezing?

---

### Post by clrg on 2010-08-08
I don't know why it crashes. I've been using Linux for years and it never ever crashed :> 

Press Alt with your left hand's pinkie and SysRq with your right hand's ring finger. Assuming  you're not 5 years old you can reach the keys with your index fingers :)

---

### Post by rocketman768 on 2010-08-08
> **clrg said:**
> I don't know why it crashes. I've been using Linux for years and it never ever crashed :> 

Years ago, individual programs used to crash from time to time. In the last few years, I have been having more and more total system meltdowns. It makes me sad inside :(

> Assuming  you're not 5 years old...

Doh, caught!

---

