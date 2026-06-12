---
title: "Speeding up startup w/ READAHEAD"
date: 2005-12-19
forum: Desktop Environments
---

### Post by ashrack on 2005-12-19
> Those who are familiar with Fedora know what 'readahead' and 'readahead_early' are. They start during the init process, caching key files during startup while no hard disk is being used (i.e. hotplug time, DHCP time)

After readahead is done, Fedora is able to start GNOME in less than 5 seconds!
Got this from here:
[http://ubuntuforums.org/showthread.php?t=6030&highlight=readahead](http://ubuntuforums.org/showthread.php?t=6030&highlight=readahead)

I personally have disabled it from INIT following this guide:
[http://ubuntuforums.org/showthread.php?t=89491&highlight=boot](http://ubuntuforums.org/showthread.php?t=89491&highlight=boot)

What do U guys thing, does READAHEAD make a difference?

---

### Post by KingBahamut on 2005-12-19
Ive run Readahead with respect to Fedora Core and RHEL here at work. I really have noticed THAT much of a difference with respect to overall functionality and responsiveness.

---

### Post by ashrack on 2005-12-19
what about with UBUNTU?

---

### Post by KingBahamut on 2005-12-19
I dont think that it would make that much difference. 

If your looking for faster read times for specific applications perhaps it might, but if your looking for faster boot time , change your UI to something less intensive or change your sysv conf to offload unnessecary services. Those two items alone can decrease the amount of load on your box and decrease your overall load times. 

As said, if your looking for applications to take advantage of readahead , for the purpose of making a better behaved application, I ran it on an RHEL box and it didnt make application responsiveness any much better than I could see. For that matter, just as prelinking does with respect to OpenOffice, I dont notice an extremely large difference in response time.

---

