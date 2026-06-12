---
title: "Cached/Buffered Memory Question"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Lerxt on 2006-08-28
I'm wondering if there's a way to force a release of cached/buffered memory.    My machine seems to run it up to the limit while I'm watching DVD's (xine-ui).  Once it hits 2GB (the amount of physical RAM I have) or nearly that amount things start to slow down.  My guess is it's moving stuff out of the cache/buffer to make room for newer data and it's slowing down the player making it choppy.  The CPU load doesn't increase I'm thinking if I could force the cache to clear out it might help.

OK, new idea.  I just swapped DVD's as I was writing this and the cache and buffered memory came back down.  Video is still really choppy though.  Any ideas?

---

### Post by Lerxt on 2006-08-29
Bumping this because I'd really like to get some input.

I took the day off from work yesterday and relaxed.  Watched a whole bunch of DVD's.  I also was watching the system monitor to see what was going on.

Here's what happened.  As long as I did nothing other than watch DVD's everything ran fine.  The cached memory and buffered memory would run up to about 1.5GB and hang out there.  Completely acceptable.  If I shut down Xine and restarted it everything was fine as well.  While watching a DVD I could open another app (Firefox, OpenOffice, etc.) and everything would remain ok.  

It was this sequence of events that seemed to cause problems:

1)  Open Xine and watch a DVD
2)  While the DVD is playing open another app
3)  Swap DVD's or restart Xine

I don't know enough about how Linux manages memory (let alone how specific apps do so) to be able to diagnose this but I'm leaning towards memory fragmentation.  Is there a way I can test this out or a way to "defrag" the memory to see if that would resolve the problem?

---

### Post by az on 2006-08-29
> **Lerxt said:**
> 
I don't know enough about how Linux manages memory (let alone how specific apps do so) to be able to diagnose this but I'm leaning towards memory fragmentation.  Is there a way I can test this out or a way to "defrag" the memory to see if that would resolve the problem?

I would think that the memory management is the most efficient if it uses as much ram as it can and never really kept any free unless it was really needed.  Forcing the kernel to keep more memory free would slow your system, rather than making it faster.

Try this:
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

---

### Post by Lerxt on 2006-08-29
DMA is "On" for the dvd drive.

Any other ideas?

---

### Post by az on 2006-08-29
> **Lerxt said:**
> DMA is "On" for the dvd drive.


Bummer.

---

