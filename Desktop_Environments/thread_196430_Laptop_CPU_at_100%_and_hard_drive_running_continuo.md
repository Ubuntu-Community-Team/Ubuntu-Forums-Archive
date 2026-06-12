---
title: "Laptop CPU at 100% and hard drive running continuous since updates 2 days ago"
date: 2006-06-14
forum: Desktop Environments
---

### Post by GadgetsGuy on 2006-06-14
The title pretty much sums it up ....

Ubuntu notified me of updates 2 days ago, so I installed them, and now ever since, my CPU is spiking repeatedly to 100%, and my hard drive is continuously running (swapfile I am guessing ...)

I cannot run on battery power for more than 20 mins :(

My lappy is Dell Latitude CPx 750 with PIII-750 and 256MB RAM, and I am running the 686 kernel.

Until the last update(s), I had been bragging to everybody how fast my laptop was using Ubuntu, but now everything HANGS ... it is choking for resources.

Unless there is a fix for this, is it possible for me to "roll back" to 3 days ago when everything worked?

I'd really hate to have to go back to Win2000 for another 6 months until Ubuntu is ready ... I hope there is a better option??

GG

---

### Post by rbalfour on 2006-06-14
[QUOTE=GadgetsGuy]The title pretty much sums it up ....

Ubuntu notified me of updates 2 days ago, so I installed them, and now ever since, my CPU is spiking repeatedly to 100%, and my hard drive is continuously running (swapfile I am guessing ...)

I cannot run on battery power for more than 20 mins :(

My lappy is Dell Latitude CPx 750 with PIII-750 and 256MB RAM, and I am running the 686 kernel.

Until the last update(s), I had been bragging to everybody how fast my laptop was using Ubuntu, but now everything HANGS ... it is choking for resources.

Unless there is a fix for this, is it possible for me to "roll back" to 3 days ago when everything worked?

I'd really hate to have to go back to Win2000 for another 6 months until Ubuntu is ready ... I hope there is a better option??

GG[/QUOTE]

What were the update you made?

Can you post the info from top?

$ top > top.txt

Then post the top.txt here.

---

### Post by GadgetsGuy on 2006-06-14
sure .... as soon as the laptop unhangs itself :(

CPU is stuck at 100% for 3 mins now since I hit the post reply button ...

It is coming ..... eventually

---

### Post by GadgetsGuy on 2006-06-14
well after 10 minutes the system is still totally frozen, so I am gonna reboot and try to paste it again...

---

### Post by GadgetsGuy on 2006-06-14
OK ... the resulting file was much larger than the 30K limit here, so I uploaded it

[http://www.ceweblogs.com/top.txt](http://www.ceweblogs.com/top.txt)

---

### Post by jerinjoy on 2006-06-14
The solution in this post looks like its related to your problem.
[http://www.ubuntuforums.org/showthread.php?t=194833](http://www.ubuntuforums.org/showthread.php?t=194833)

Apparently SMP support which is enabled in the 686 version causes high CPU usage.

---

### Post by GadgetsGuy on 2006-06-14
yes I just found that thread also ...

now how do I edit the rc.local file (I am permissions retarded) :(

---

### Post by GadgetsGuy on 2006-06-14
OK ... I found a HOW to to edit other config files with sudo gedit, so I am giving it a try ...

wish me luck ...
GG


EDIT: I sucessfully edited my rc.local to add that line, whoever after a reboot my hard drive is still winding away, and my CPU is still spiking

---

### Post by GadgetsGuy on 2006-06-14
any idea when this issue will be corrected?

I am at a crossroads ... I really like Ubuntu, but now it is hampering my productivity ... I no not WANT to go back to Win2000 for another 6 months, but I have my doubts if Ubuntu is ready yet.

I cannot have my laptop hard drive spinning 24/7 while Ubuntu runs :(

---

