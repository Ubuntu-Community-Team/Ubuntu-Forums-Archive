---
title: "How to tell if problem is a kernel crash or hardware issue?"
date: 2009-02-04
forum: General Help
---

### Post by liquidpele on 2009-02-04
Every once in a while, my computer just dies.  The box has power, fans are spinning, but the monitor looses video and I can't SSH to the machine anymore.  

I've looked over the kern.log and syslog, but I don't see anything there regarding what happened.  It just has the usualy -MARK- stuff, and then the startup information.

Can anyone recommend the best way to debug this?  Does it sound like a hardware issue, or can the kernel crash like that and not even leave a dump or a panic message in the logs?  Any help would be much appreciated.

I'm running 8.10 Desktop edition, but using the 8.10 server kernel (vmlinuz-2.6.27-11-server) so it will see all 4 GB of my RAM.  I can't get it to reproduce at will, it seems fairly random and only happens about every week or two but it's infuriating when it happens.

Any help would be greatly appreciated!

---

