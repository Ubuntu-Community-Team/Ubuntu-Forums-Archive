---
title: "how to debug a possible kernel crash"
date: 2009-05-04
forum: General Help
---

### Post by spip on 2009-05-04
I've been running ubuntu 8.10 for about 2-3 weeks on a toshiba tecra laptop.  Twice now, I've encountered a complete hang, once in gnome, once in xubuntu.  No more mouse cursor, ctrl-alt-delete would not quit x-windows, no screen updates.  I didn't have another machine handy to ping this one and see if the tcp stack was at least still responding (which is usually a quick way for me to determine the kernel is still ok).

/var/log/messages shows nothing.

The more recent crash happened as I started playing a youtube video, so possibly related to a video card driver?

In any case, I don't have much experience pinpointing the cause of a kernel crash.  Where do I start?  Could some very useful data be sitting somewhere else than /var/log/messages in a place I don't know about?

Also, I'm assuming it was a kernel crash, but I'm not 100% sure -- nothing was responding though, the machine seemed pretty dead. 

I would like to get at the bottom of this, I'm just not sure where to start.

Thanks.

---

### Post by KhaaL on 2009-05-04
Hey spip

Look at these documents: [Netconsole]("https://wiki.ubuntu.com/KernelTeam/Netconsole") and [Debugging KernelOops]("https://wiki.ubuntu.com/DebuggingKernelOops"). You can see other debugging documentation at [this page]("https://wiki.ubuntu.com/DebuggingProcedures"). 

Good luck!

---

