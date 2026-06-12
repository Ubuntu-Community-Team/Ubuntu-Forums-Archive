---
title: "Old computer hangs during halt."
date: 2006-06-06
forum: Desktop Environments
---

### Post by Mamour on 2006-06-06
Hi all,

I'm having another issue with dapper on an old computer of mine. When I try to shutdown the machine, the process seemingly locks up at the "Will halt now" step, i.e. the last one, and the machine does not actually halt.

This worked under breezy, and stopped working after my recent upgrade to dapper.

Any tips on how to make this run again?

Thanks!

---

### Post by Hiroshima on 2006-06-06
I was just about to start a similar thread.  Same problem. Last three steps say:  

Unmounting File Systems -- Ok
Deactivating Swap -- Ok
Will now halt -- (hangs here)

Looking forward to any ideas,

Hiroshima

---

### Post by nicolas314 on 2006-06-06
Same thing here: shutdown stops after "Waiting to shutdown",
sometimes after "stopping all md devices".
Machine worked perfectly well with Breezy.

I have been browsing through the forums, there are some relevant
discussions in the Dapper beta forums but apparently nothing coming
out. The only certainty is that it happens on very different machines.

Bad thing is: I have to say this is not the only thing that stopped
working in Dapper. While it was in beta I would still be tolerant, but
now it gives the image of an unfinished business released too soon.

---

### Post by Hiroshima on 2006-06-06
After a little more poking around, I found these:

[http://ubuntuforums.org/showthread.php?t=189498&highlight=hang+halt](http://ubuntuforums.org/showthread.php?t=189498&highlight=hang+halt)

[http://www.ubuntuforums.org/showthread.php?t=187186](http://www.ubuntuforums.org/showthread.php?t=187186)

[http://ubuntuforums.org/showthread.php?t=166591&page=2&highlight=hang+halt](http://ubuntuforums.org/showthread.php?t=166591&page=2&highlight=hang+halt)

Bug list
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961)

Will have to hope they find a solution soon, until then, I think the answer was "turn off the power"- 
Hiroshima

---

### Post by Hiroshima on 2006-07-07
I had to reinstall, and did do with a Dapper Kubuntu.  After that the problem was solved.  I think it is the same kernal, so it must have been the reinstall.  Might be worth a try.  Just remember to backup your important stuff first.

Hiroshima

---

