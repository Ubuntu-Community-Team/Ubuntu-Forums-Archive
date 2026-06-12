---
title: "Random stutters in games and desktop"
date: 2007-10-26
forum: Desktop Environments
---

### Post by usp8riot on 2007-10-26
In XP, when something's using a few resources, it just makes things a tad less snappy. Say, something's using %10 cpu but I've tried many different things like turning off compiz, any apps using any cpu, etc. Is it just the framework of linux that instead of smoothing the responsiveness, it lets an app use a lot of resources for maybe a microsecond on and off or something? Should I increase the priority of my fps game so it won't stutter? I have an overclocked XP2800, nvidia 6800gt, and 1 gig low-latency ram with the binary Nvidia drivers so it's enough to run Enemy Territory. Anyone know if this problem is solvable? 

On second observance, it seems Amarok now uses maybe 70% cpu sometimes for a second, more or less. I've noticed a few more apps doing this also. Is this normal?

---

### Post by prshah on 2007-10-26
I found a huge performance improvement (smoother desktop flow, faster ring-type switching) by adding the below line to the device section in my /etc/X11/xorg.conf:

Option "UseFBDev" "true"

Also check if DMA is enabled on your HDDs?

HTH

Cheers,
PRS

---

### Post by usp8riot on 2007-10-26
Yes, DMA is enabled. And after googling, I was skeptical of the UseFBDev option as it seems an older solution and seemingly more for ATI cards. Actually, I did notice some improvement but that's after restarting and not having firefox going and Amarok with a huge playlist. I was trying to play with Amarok playing also but still, it should still be no problem for a game of that easy on resources to play an mp3 on my average hardware.

---

### Post by prshah on 2007-10-27
Another issue that I faced was that Swap was not enabled after I attempted (and failed at) hibernation...

maybe you can verify if swap is active:

swapon -s

?
Priyasen Shah

---

### Post by usp8riot on 2007-10-27
Yes, it is enabled. It doesn't do it unless something is eating up some cpu resources. Maybe 30% or something. But in Windows, even if something is using up 80%, I don't get stutter using the desktop, just less responsiveness. It's just really annoying. Just wondering if there was a work-around like decreasing the priority of Kwin or KDE desktop manager or something.

---

