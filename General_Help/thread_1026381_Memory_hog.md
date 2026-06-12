---
title: "Memory hog?"
date: 2008-12-31
forum: General Help
---

### Post by lnajt on 2008-12-31
I was cleaning up my computer, and I found that Linux had allocated 4.58 GBs of space to the linux-swap. Is this gratuitous - can move some of that storage space to my primary partition or should I just leave it alone?

I have 2 gigs of ram on my laptop, which I use primarily for school work and multimedia.

Thanks.

---

### Post by jrusso2 on 2008-12-31
With that much memory your wasting a gig of space but if its not a problem I would leave it if you have lots of room.

---

### Post by s3a on 2008-12-31
If it's 32 bit you can definetely lower it. Even with 64 bit you can do really well with 2-3GB swap. In addition to that (after that), do:

1) sudo -i
2) apt-get install preload
3) gedit /etc/sysctl.conf
4) on the sysctl.conf file, add the following without the quotations at the bottom of the file:
"vm.swappiness=0
vm.vfs_cache_pressure=0"

*That should increase your performance A LOT! Preload preloads applications to your RAM based on usage so that your applications launch faster and swappiness and cache pressure of 0 just make your swap be used only if you're running out of total RAM and it doesn't just try to keep lots of stuff cached by putting frequently accessed data in the hard drive (which slows down usage).

---

