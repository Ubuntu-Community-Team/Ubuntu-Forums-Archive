---
title: "system hangs (HOTPLUG SUBSYSTEM) newbie"
date: 2005-10-17
forum: Desktop Environments
---

### Post by loopymonkey on 2005-10-17
hello, i recently re-installed ubuntu 5.10 after a successful run of 5.04 on a Dell laptop CPI PII 400mhz with 128 megs of ram.  But after a successful install, 5.10 during the boot process will 8 of ten times hang during 'hotplug subsytem" configuration when the black screen is up with ubuntu logo.  Is there something i can turn off during startup or disable something to allow a good boot?  Thanks!

I should add that this did happen some with 5.04 but not all that often. I would just reboot and usually after 1-2 max reboots it would stop hanging and startup.  With 5.10 this seems to happen almost everytime with startup.  A lot more common.

---

### Post by GeneralZod on 2005-10-17
Do you have any USB devices plugged in at all?

---

### Post by loopymonkey on 2005-10-17
just a wifi PCMCIA card that works great with ubuntu 5.04/5.10.  that's it.

---

### Post by WolfJay_83 on 2005-10-17
This is a recurrent issue that seems to happen spurraticaly on several laptops with both 5.10 and 5.04.

I have had the same problem with my Dell Latitude LS(spurradicaly in 5.04 and continualy in 5.10preview).  I hope somone out there has a be-all end all solution for this, but here is what I know about it.

It has something to do with loading the modules for such things as your Ethernet, USB, or PCMCIA cards. If it cant load one, it just locks, I dont know who programmed such a device loader, but it seems rather silly to make something without failsafes.  So, one suggestion is unplug everything you can, and try it.  If it works, you might be able to figure out which is causing the problem, and get new drivers for it.

If you want your machine to boot, you need to press CTRL + C as soon as you see "Starting Hotplug Subsystem."  You have about .5 seconds to cancel it before it locks your machine. Note: you will not have any access to network, USB or PCMCIA cards when you load this way.

Some posts from 5.04 advocated putting extra arguments in your boot loader, I have tried these with limited success.  Doing the CTRL+C thing will allow you to get into the system to do this.

Blacklisting modules is also advocated in many of those posts.  This, again, I have had limited success with.

I dont want to give instructions for doing either of these because I realy dont understand what they are doing well enough to tell you properly- hopefully someone will reply who knows a little more.  But If you get limited responses in this forum, I would suggest searching the 5.04 forums as there are many threads associated with this *recurent* problem.

Ubuntu has impressed me with everything... except this problem.  I wish you luck in figuring it out.

btw, on my dell, it appears that the ethernet drivers cause the problems.

Regards,
Jason

---

### Post by loopymonkey on 2005-10-20
The CNTRL-C does seem to work if i do it at the right time.  then after that though my sound is disabled.  I'm going to try and test someone's theory on this only occuring when booting off battery.  someone in the forums wrote this hotplug doesn't occur when booting while plugged into AC.  I'll see what happens...  5.10 DOES seem to definiltey hang more then 5.04 though for the hotplug.

---

### Post by jackmacokc on 2005-10-20
[QUOTE=loopymonkey]hello, i recently re-installed ubuntu 5.10 after a successful run of 5.04 on a Dell laptop CPI PII 400mhz with 128 megs of ram.  But after a successful install, 5.10 during the boot process will 8 of ten times hang during 'hotplug subsytem" configuration when the black screen is up with ubuntu logo.  Is there something i can turn off during startup or disable something to allow a good boot?  Thanks!

I should add that this did happen some with 5.04 but not all that often. I would just reboot and usually after 1-2 max reboots it would stop hanging and startup.  With 5.10 this seems to happen almost everytime with startup.  A lot more common.[/QUOTE]

I had this issue as well, but it was on a Dell GX260 Desktop - and occured when I switched from AGP graphics to a PCI graphics card.

---

### Post by Dajazzz on 2005-10-22
I have the same problem on my DELL LATITUDE LS (500mhz)

weard thing is that it happens sometimes not. Just taking the battery out of it and restart it. workst about 1 on 4 times....

---

### Post by loopymonkey on 2005-10-22
yes, unplugging the AC didn't really have any big effect.  I think it's a matter of turning on/off or editing some hotplug modules is my best guess.  Which ones or how to even edit is something i'll wait for someone else to figure out!  

I did notice that if I CNTRL-C when i see hotplug loading and that cancels and the boot works and i login, i will not get sound.  But most every time AFTER this I restart THEN it boots good.  
 
Ubuntu is still the most solid distro on the laptop i've tried (Vector, Puppy, Linaire, Suse, PC-BSD, SLAX, Knoppix).  Vector works very fast, but got complicated when my wifi didn't work, and puppy wasn't installing easily to the hard drive and i didn't want it to take up the cd all the time.  And it's also a bit ugly looking.  Ubuntu is definitely a cleaner install, setup and config.  If only the hang could get fixed.  ;)

I am going back to Hoary, 5.04 though until this gets sorted out. It's too much of a pain for reboots to hang so much.  Things went better with 5.04.

---

