---
title: "Firefox and Opera freeze frequently"
date: 2009-03-31
forum: General Help
---

### Post by tomasito on 2009-03-31
Hi,

recently I changed from Windows to Ubuntu 8.10 and I still work on a good configuration of my system.

I have a problem with my web browsers, in the beginning I only used firefox 3.0 (just updated to 3.08 ), but later I also installed Opera (9.64) to check if the occuring porblem appears in both browsers, and it does!

Here the problem, the browsers frequently freeze the window (window get transparent gray) when loading pages, even when they already finished loading the pages. The freezing can take some seconds, some minutes or the program won't reactive at all. So, I have to shut it down manually and restart it. When I restart it, I choose to restore the previous session and the pages load without problem.

Anyone knows this problem or knows where I have to search to solve the problem?

---

### Post by paradigm2 on 2009-03-31
Hmmm. From experience I would suggest that you go to the system monitor and check resources when you have these browsers open.  At the top of the screen, System -> Administration -> System Monitor.

Check particularly the CPU usage and memory.  If they are near the top then that is probably the immediate issue.  If this is the problem let us know and maybe we can go from there to possibly help fix it.

---

### Post by tomasito on 2009-04-01
It is not a problem of ressources; the two CPU cores show normal occupancy far away from 100%, the total memory usage is not reaching the limit and swap memory is not used. In the processes firefox CPU usage is 0-1% and memory usage is normal as well. 

When firefox freezes I can continue working in with other programs without problems. There isn't a connection problem either, because skype keeps running normal. I can even start Opera and use it normally, even if firefox is frozen. This also works vise-versa, so when Opera freezes.

Any idea??

---

### Post by WilliamJenningsBryan on 2009-04-01
Do you have the Flash plugin installed? This can make your browser crash frequently, particularly if you're using an experimental version.

---

### Post by tomasito on 2009-04-01
Yes, I have the adobe flash plug-in installed. I am not really sure about it, but I think, I need this plug-in for see a lot of internet sites which includes videos or animations, right?

Or is there an alternative plug in I could use?

---

### Post by tomasito on 2009-04-03
I deactivated the flash player and the freezing occurs less often, but it still occurs. However, deactivating the flash player is not really a solution, I just realzied how many sites it use.

---

### Post by ceejay on 2009-05-03
Hi

I'd just like to add that I have exactly the same problem - although I am on Ubuntu 8.04, with Firefox 3.0b5, Opera 9.64.

Like OP I have plenty of resources - only modest CPU usage when this is happening, using 25% of my 2GB of memory, only tiny network activity.

Other applications seem to work ok throughout the browser freeze time, which like OP can be anything from a second to a minute.

It used to work once! I'm not sure though exactly when it started or what change had then occurred.

Anyone have any ideas - this is driving me nuts!

TIA

---

### Post by stinger30au on 2009-05-03
> **tomasito said:**
> Hi,

recently I changed from Windows to Ubuntu 8.10 and I still work on a good configuration of my system.

I have a problem with my web browsers, in the beginning I only used firefox 3.0 (just updated to 3.08 ), but later I also installed Opera (9.64) to check if the occuring porblem appears in both browsers, and it does!

Here the problem, the browsers frequently freeze the window (window get transparent gray) when loading pages, even when they already finished loading the pages. The freezing can take some seconds, some minutes or the program won't reactive at all. So, I have to shut it down manually and restart it. When I restart it, I choose to restore the previous session and the pages load without problem.

Anyone knows this problem or knows where I have to search to solve the problem?


check your hard drives first

i had this and very soon afterwards i got clunking from the hdd

it was on its way out

i copied data off it, put in new hdd, and it has not skipped a beat yet

---

### Post by tomasito on 2009-05-07
I checked my hard disk, I can't see any problem with them. Both partition have several GB of free space. 

So, any other guess?

---

### Post by argraff on 2009-05-14
I'm having a similar problem, although mine is primarily freezing with Opera 9.64 and during the freeze (and after force quit) it's hogging 60%+ of my CPU. I then lose Compiz functions, and Gnome Do. I'm on 9.04. Any clues? I've given up on Opera for the moment.

---

### Post by DeMus on 2009-05-14
> **argraff said:**
> I'm having a similar problem, although mine is primarily freezing with Opera 9.64 and during the freeze (and after force quit) it's hogging 60%+ of my CPU. I then lose Compiz functions, and Gnome Do. I'm on 9.04. Any clues? I've given up on Opera for the moment.

Try to disable that horrible Compiz and see if you still have those problems.

---

