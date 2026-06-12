---
title: "Ram and performance, enhancement?"
date: 2009-04-28
forum: General Help
---

### Post by bruceschaller on 2009-04-28
Recently, Toms hardware had an article about how little having more than 6gb of memory actually accomplished. [http://www.tomshardware.com/reviews/memory-module-upgrade,2264.html]("http://www.tomshardware.com/reviews/memory-module-upgrade,2264.html") I found this very interesting.  

I've also been reading up about improving performance of my browser, which normally caches to /tmp by using a tmpfs ramdisk. [http://ubuntuforums.org/showthread.php?t=1054129&highlight=ramdisk]("http://ubuntuforums.org/showthread.php?t=1054129&highlight=ramdisk")

With memory prices at historic lows, and a new file system ext4 which has a delay when writing to disk anyway, ram seems an inexpensive option to get SSD (or better) performance just by adding a few sticks of cheap ram.

I am not really interested in abandoning my hard drive just yet!  I like the storage, it's expansive and reliable.  I am simply want the fastest computer possible to do my daily tasks with.  I wish that firefox, openoffice, any application that I've opened in the past 3 days, be precached in ram to the greatest extent possible, along with as much kernel is practicable. (Excuse my lack of knowledge in advance on where the kernel usually hangs out, if I'm mis-speaking.)

Maybe a liveCD is the way for me to go. To me the best computer is simple to use, and very quick at getting where I want to be.

How would you go about achieving this?

Would it be possible to have a separate partition of about 2-3GB load itself into ram on boot, like a split / and /home? Could / fit? If changes were made, how would they be reflected later? Lost on boot?  Is there a way that I could preserve the changes on shutdown? Ubuntu-HiTest might be a fun distro for people who have a lot of ram for very peppy performance. 

Thanks

---

### Post by kerry_s on 2009-04-28
everything is put in ram once you use it, if nothing else needs the ram it will stay there. you can tweak it i use this:

```
vm.overcommit_memory = 1
vm.overcommit_ratio = 95
vm.dirty_ratio = 5
vm.swappiness = 1

```

in /etc/sysctl.conf to keep things in ram longer. now if you don't turn off your computer it should always be fast, i use suspend for mine, along with the usual gnome tweaking for lower resource and replacing the heavy programs with lighter alternatives. i don't have a lot of memory though, i have 256mb on my laptop and 1gig on the desktop.

---

### Post by dcstar on 2009-04-29
> **bruceschaller said:**
> Recently, Toms hardware had an article about how little having more than 6gb of memory actually accomplished. [http://www.tomshardware.com/reviews/memory-module-upgrade,2264.html]("http://www.tomshardware.com/reviews/memory-module-upgrade,2264.html") I found this very interesting.  
........

Why?, it was a Windows Vista test and has little relevance to Linux.

---

### Post by bruceschaller on 2009-04-29
Thanks kerry, I'll give it a shot!

---

