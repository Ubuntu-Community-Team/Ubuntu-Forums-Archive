---
title: "system freeze at least once a day in 8.10--log?"
date: 2009-01-04
forum: Desktop Environments
---

### Post by aaronLund on 2009-01-04
Hi all.

I'm getting mysterious (seemingly) random screen freezes every day.  When I go to bed at night, it's a given that I'll wake up to a frozen screensaver.  That means a hard restart at least once a day.  Can't imagine that's doing anything good for my hard drive...

I have a feeling this has to do with my nvidia geforce 5200 and envy (which I've installed and got working.  So, yes, desktop effects are indeed happening even with this video card). 

I'm pretty sure these freezes were happening before I installed envy, however.  I thought they'd go away once this issue was fixed....not so lucky.

Also, I still cannot shutdown or restart my computer without doing a hard restart.  It just hangs at that "acpid exiting" (or something to that effect).  

So I was hoping that my messages.log might be worth looking at by someone.  Oddly enough, the whole system froze on me yesterday (Jan 3 '09) and I restarted around 9:50 am.  So, technically, this isn't a freeze exactly like the ones I've mentioned above ("screen saver freezes") but I'm willing to bet they're related.  The odd part was that I was sitting in front of the computer when this one happened.  

So, here's my log.....please note that I restarted at 9:50 am around line #1154.

Link=> [http://aaronlborg.pastebin.com/f280fce3a](http://aaronlborg.pastebin.com/f280fce3a)

(sorry for the doubled line numbers.....i wasn't aware that paste-bin added these. nice.)

Thanks for any help!
-Aaron

---

### Post by Jameshardy88 on 2009-01-06
im having a similar problem i seem to get a random freeze once a day for no apparent reason

---

### Post by bunty on 2009-01-06
The first thing to check is hardware failure. Get a liveCD of some sort and run memtest86 for a day or so. It that runs without a clitch try cpuburn test suite but make sure you keep close eye on your cpu temps and you are ready to cntl-C the progs it things get too hot.

If you can do that without any locks or failures , then start trying to look for a software issue, not before.

---

