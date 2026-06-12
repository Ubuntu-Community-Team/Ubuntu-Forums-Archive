---
title: "Why is my memory leaking?"
date: 2009-04-30
forum: Desktop Environments
---

### Post by elmagno on 2009-04-30
Applies to both Intrepid and Jaunty 64. Video is ATI HD3300, drivers are 9.3 and 9.4. Processor is Phemon II. Problem:

With compiz on, memory starts at around 440Mb and immediately begins to build. Right now I'm at 2Gb after about 3 hours. Switch to Metacity and memory is released. Switch back to compiz, leaking starts again.

Where ever this memory is going, it's not apparent from any PID.

---

### Post by elmagno on 2009-05-01
Bump

---

### Post by hardyn on 2009-05-01
is it leaking, or just being used?

---

### Post by FlyingBuzz on 2009-05-01
This is absolutely normal. One part of your memory is used by programs and the other is used as a cache. This causes better perfomance. And when you launch a huge application which needs lots of memory, a part of RAM which belongs to cache reduces and gives enough free space to an application.
P.S. Sorry for my English, I'm from Russia, I've just registered and I'm glad to become a part of Ubuntu Community =)

---

### Post by inobe on 2009-05-01
this depends on the amount of memory you have ?


it's nice to have 8gigs in memory to see 4gigs in cache !

---

### Post by elmagno on 2009-05-01
Thanks for the responses, but no. I disabled compiz completely and now no memory leak at all. What I am thinking (pure speculation) is that the leak is coming through the ATI driver via Compiz. But I know of no way of tracing this, even if it is true.

But it's not a caching thing, and it's quite deadly--eats up a whole 4Gb in about six hours.

---

### Post by Parp on 2009-05-02
I'm finding Xorg using a huge amount of RAM if system left on for days... Again ATI HD3450.. seems the driver is causing all sorts of issues... (posted a few times about various other issues with ATI driver in Jaunty)..

---

### Post by elmagno on 2009-05-02
Yes, I've seen several postings on the Xorg memory problem, too. In my case, the memory that's eaten up is not associated with any running process that I can see in gnome-system-monitor or top. "free -m" shows a reasonable amount of caching, but also shows a couple of gigs used that can't be accounted for after compiz has been running a while.

---

### Post by practic on 2009-05-16
> **elmagno said:**
> What I am thinking (pure speculation) is that the leak is coming through the ATI driver via Compiz. But I know of no way of tracing this, even if it is true. But it's not a caching thing, and it's quite deadly--eats up a whole 4Gb in about six hours.

I see the problem also and am using the Nvidia proprietary driver, so it is probably not related to the ATI driver itself...perhaps something interacting with the graphics driver.

I just tried toggling Compiz off via the Fusion-Icon, and I still see cache memory climbing. Shouldn't that eliminate compiz from the suspect list? I don't see it on the list of Processes in System Monitor...

---

