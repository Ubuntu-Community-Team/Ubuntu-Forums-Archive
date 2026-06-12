---
title: "did XGL kill my ubuntu or was it killed by powering off without shutdown?"
date: 2006-07-26
forum: Desktop Environments
---

### Post by rene100 on 2006-07-26
I'm a Ubuntu (and linux) noob and I've been messing around with an installation for a few days now. I had almost everyting working perfectly (finally got fglrx working!) and decided it was time for Compiz + XGL. I installed it using a simple howto that involved creating a .Xsession file in my /~ It worked and it was beautiful for five minutes, until I left the room. When I came back the screen had gone white (maybe a screensaver loaded and messed with the XGL?) I couldn't figure out what to do so I rebooted... The file system on reboot had to some self repair, and now everything has gone funny... First of all, the compiz effects are all gone, second my internet doesn't work (except I can go to [www.google.com](www.google.com) and perform searches?!? but no other website will load) When I go to shut down, it only gave me the option of switching users.....

I decided to revert back by deleting the .Xsession file and that fixed the missing "shut down / reboot" options, but the internet is still messy.

Is this because of the improper shutdown? I had heard in the past that that could seriously mess up linux, is this why everything is gone? For future reference, is there anything else I can do? (PS I tried hitting ctl-alt backspace when i had the white screen and it didn't help)

please help!!

---

### Post by cptnapalm on 2006-07-26
X lock ups have been, for a LONG time, a weakness of Linux.  While the underlying system is rock solid, X can really screw things up.  You are not alone!

But on to your problem.

I would say that the first thing to be done is to do this: ls -l /lost+found

If there is anything in there, then something was potentially messed up.  That's where stuff goes when the filesystem has had a problem and does not know where to put the junk it found.  A rather appropriate name, really.

---

### Post by rene100 on 2006-07-27
thanks for the tip.  I actually gave up and ended up backing up my data and reinstalling ubuntu.  I guess that's the cowardly way out, but honestly, I don't even know where to beging troubleshooting the problem since I'm so new to linux.

---

### Post by Soarer on 2006-07-27
Just as an aside, my electricity supply is overhead through a nearby copse. Fairly frequently one the tress will fall & take a power line out (4 times in the last cople of months). So I often have unplanned shutdowns :).

So far I have never had a problem with rebooting after the power comes back, except for my routers, which often crash & need a further power cycle, so I doubt it was that which directly caused the problem.

---

### Post by mozetti on 2006-07-27
> **Soarer said:**
> Just as an aside, my electricity supply is overhead through a nearby copse. Fairly frequently one the tress will fall & take a power line out (4 times in the last cople of months). So I often have unplanned shutdowns :).

So far I have never had a problem with rebooting after the power comes back, except for my routers, which often crash & need a further power cycle, so I doubt it was that which directly caused the problem.

It might not be a bad idea to get an uninterruptible power supply (UPS) - I'm picking one up in the next couple of days. The brand APC has good Linux support via a 3rd-party daemon, APCUPSD (APC UPS Daemon) and it's available in the repos (though you may need universe/multiverse enabled).

---

### Post by Soarer on 2006-07-27
Thanks for the good suggestion. I have thought about it but it would need to run several computers, 2 routers, WAP etc. to be useful. And since it causes me few problems when it does go, apart from not being able to work :), I haven't yet done it.

But I think I will.

---

