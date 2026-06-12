---
title: "slow interface"
date: 2013-12-22
forum: Desktop Environments
---

### Post by ash252.rocks on 2013-12-22
Hey guys!
I recently installed xubuntu 12.04LTS
but i have found that the interface - app laoding speeds, maximise minimise and everything else is sluggish and feels unresponsive
i never had this problem with Win 7 .. even though it would start to slow down if i ran a lot of apps at once
i checked the ram usage and its usually at 30-40% when i am browsing around 2-3 tabs in chromium
My system specs are :
Intel Dual core 1.73Ghz 
1 gb ram 
           the last time i had installed linux(mint) , it ran flawlessly, even though it had some bugs.. So I'm wondering how to improve the performance of my laptop ..
thanks in advance 
cheers!
 and also some apps like Preload keep crashing as soon as i open them.. should i try a clean install?

---

### Post by Tristan_Williams on 2013-12-22
What is your kernel version, and installed packages?
You can get a list of installed packages with the following command
```

sudo dpkg --get-selections >> ~/pkg-list

```
Just include the ~/pkg-list file in your next reply.

---

### Post by TheFu on 2013-12-22
1G of RAM is sorta minimal for a system today unless you keep fewer than 5 apps running - that is just a guess. Some apps are heavy on RAM and will suck up everything on the machine by themselves.

Without actual facts and data, we can't really troubleshoot your system. What sort of monitoring do you have running?  Disk I/O, swapping, network I/O, missed cache hits, total number of files open, CPU and RAM per process?  Monitoring with SysUsage (or similar) would be a huge help.

On a box with 1G of RAM, I'd be certain to monitor virtualmemory use carefully.  How large is your swap file? 
**swapon -s** will be helpful to get started.

---

### Post by Yellow Pasque on 2013-12-23
Are you using the xfce compositor? Have you tried running without it?

---

