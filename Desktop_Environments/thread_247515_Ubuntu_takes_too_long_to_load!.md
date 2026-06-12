---
title: "Ubuntu takes too long to load!"
date: 2006-08-30
forum: Desktop Environments
---

### Post by --cona-- on 2006-08-30
For some reason when i choose to use ubuntu on my pc it takes about 15mins but if i choose the use xp it takes 2mins? :S

---

### Post by rondeth on 2006-08-30
Any messages which seem to indicate what's going on? My laptop took forever to start due to the checkfs.sh script (doesn't like something about my fat32 partition)...around 8 minutes on that step alone in my case. 

Anyway, without any more details, it would be difficult to hazard accurate guesses. Cheers.

---

### Post by madmetal on 2006-08-30
look if dma is on at your hdd and try have a better system with apt-get autoclean.
look also if ubuntu tries to find network connections which sometime can take a lot time..

---

### Post by AntiFlash on 2006-08-30
ubuntu by default loads all sorts of daemons that you might not need... power management (might not need if you're not on a laptop or if you don't have a UPS)...bluetooth...RAID...PCMIA...etc when ubuntu is loading, read all of the various services that it loads and determine whether or not you need them.  from there, you can re-config your install without those services running at boot time which should make your system boot time drop significantly.  

the aforementioned FS check is something that will definitely extend the time required to boot.  it is supposed to happen every 30 boots and/or when the system does not shutdown nicely to minimize the opportunity for file system corruption...not sure how to configure the boot FS check options...

---

### Post by kircher on 2006-08-31
check out this thread. It may help you. read it carefully though. I disabled a lot of services I didn't need, and my boot time was significantly lessened. It's still not as fast as XP, but XP cheats and displays the desktop before everything is loaded. 15 minutes is a long time though...

---

### Post by kircher on 2006-08-31
sorry, didn't actually quote the thread in the last post. Here it is [http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)

---

### Post by --cona-- on 2006-08-31
Thank-you for your help. ;)

---

