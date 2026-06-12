---
title: "Cache memory tuning?"
date: 2009-01-02
forum: General Help
---

### Post by niallporter on 2009-01-02
Hi all,

I currently run Hardy x86_64 on my machine, hardware is as shown below in my sig.  I sometimes have to run Windoze apps so I have an XP Pro install in a VMWare virtual machine to which I've allocated 512Mb of RAM.  The problem is that when I start doing stuff with the VM, the whole system (i.e. the host OS) slows to a crawl as the machine begins swapping constantly.

I managed to ssh in to the host from another machine and ran the "free" command but couldn't grab the output to paste here.  It looked like roughly 65% of physical ram was "cached", around 10Mb of it was "free".  Swap partition on this machine is 1Gb also and around half of that was being used.

It occurred to me that I don't really want 65% of my physical RAM being used for cache if that's going to mean that under higher memory load the system has to swap constantly.  Can someone give me some direction on how to tune this and suggest values that maximise availability of physical RAM for interactive applications rather than caching?  I'm aware of some of the things that can be tweaked using sysctl or in /etc/sysctl.conf but I'm having a hard time finding suggestions for starting points for desktop machines (most tuning guides on the web seem to be directed towards sysadmins tuning servers rather than desktop users)....

Any help greatly appreciated!
Niall

PS.  Below is the output from the free command immediately after boot with only the background stuff and my GNOME desktop running...  That's a lot of cache usage for nothing much happening IMHO...

```
niall@polaris:~$ free
             total       used       free     shared    buffers     cached
Mem:       1028800     869444     159356          0      53392     401512
-/+ buffers/cache:     414540     614260
Swap:      1052216          0    1052216
```

---

### Post by wmoore on 2009-01-02
I'm curious about this one too :popcorn:

---

