---
title: "Test Rig for Opera Browser?"
date: 2009-08-12
forum: Desktop Environments
---

### Post by ionFreeman on 2009-08-12
I've got really serious performance problems. UbuntuForums took about 40 seconds to load. I'm trying to figure out what's going on.

The computer seems snappy enough when I'm not doing anything internet related, but [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/) says I've got lots of bandwidth and streaming media plays fine.

(1) It could be Opera. Sometimes my text entry does seem to lag my typing significantly, suggesting some performance problem. But `sudo gnome-system-monitor` shows that I'm not really stressing the system; as I write this, CPU1 is at 50.5 % and CPU2 is at 29.2 % and memory use is around 31.2 %. Also, Firefox also sucks -- it just took 20 seconds to open [http://sluggy.com](http://sluggy.com).

So, I don't think it's Opera. But, I'd like a little local test rig to exonerate it. Is there one around?

(2) Like any Time Warner Cable customer, I'm suspicious of them. I've got 26649 kps of download speed and 487 kpbs of upload speed. Since I mostly just read text (and comics), that should be plenty. But, the internet doesn't feel faster than when I had a 56.2 kbps dialup. I should have a 500x boost in download performance, and I'm still waiting forever.

Could they be engaged in some sort of dastardly throttling, trying to pressure me to buy their turbo system?

(3) It could be this machine. I have a laptop which performs somewhat better. But, it's the same software and I don't seem to be resource constrained, so I don't really know what's going on here.

What are the current profiling tools I should be using? Is there a troubleshooting guide that sounds like it could help me? Where do I go from here?

Thanks!

Ion

---

### Post by ionFreeman on 2009-08-12
By "This Machine", I mean a ZAReason Breeze 3110 running Ubuntu 9.04 Jaunty Jackelope, Intel Atom 1.67 GB Processor, 2 GB DDR2 memory, ext4 filesystem. My Opera version is 9.64.

---

### Post by tgalati4 on 2009-08-12
Sometimes performance issues are related to the website's content.  It takes time for all of those ads, banners, and google analytics to load.  The page will only load as fast as the slowest content.  The ad content is constantly changing so it's hard to diagnose.

Find some forums or sites with no ads and additional stuff and time those loads with a stopwatch.  Keep records to see if you can pinpoint the bottleneck.

Plug in with an ethernet cable to do the tests.  That would isolate wireless interference, which comes and goes.

---

