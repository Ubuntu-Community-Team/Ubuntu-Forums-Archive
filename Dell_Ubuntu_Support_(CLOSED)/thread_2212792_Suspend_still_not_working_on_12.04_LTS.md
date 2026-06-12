---
title: "Suspend still not working on 12.04 LTS"
date: 2014-03-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by roberto03 on 2014-03-23
Hi I am using

**Distributor ID:    Ubuntu**
**Description:    Ubuntu 12.04.4 LTS**
**Release:    12.04**
**Codename:    precise**

on a Dell Latitude D600
**$ uname -a**
**Linux roberto-Latitude-D600 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:40:43 UTC 2013 i686 i686 i386 GNU/Linux**


I tried to suspend using the suggestion in:
[http://ubuntuforums.org/showthread.php?t=1978290](http://ubuntuforums.org/showthread.php?t=1978290)

but it hasn't worked yet. 
Do you have any advice? I could also switch back to 11.10 if necessary, but I absolutely need working suspend to ram.
By the way, which command from line should I use?

Please help.
Thank you very much in advance.
Roberto.

---

### Post by ajgreeny on 2014-03-23
Are you aware that Lubuntu 12.04 is no longer supported?

You should at least consider updating the OS to Lubuntu 13.10, or even looking at Lubuntu 14.04 daily image from [http://cdimage.ubuntu.com/lubuntu/daily-live/pending/](http://cdimage.ubuntu.com/lubuntu/daily-live/pending/) which even though it is only at beta stage seems very stable; not without an odd glitch or two, but nothing show-stopping.

If that is not an option have a look at the Lubuntu 12.04 deriviative LXLE, which uses the 12.04 base but adds a number of repos for the LXDE parts of lubuntu which have now lost support.  I have no idea whether or not that will overcome your suspend problem, but it uses a later kernel which might help.  You could even try a later kernel in your current Lubuntu12.04; search for 3.5.0- or 3.8.0- kernels in synaptic and install the appropriate one to see if it helps out.

---

### Post by roberto03 on 2014-03-23
> **ajgreeny said:**
> Are you aware that Lubuntu 12.04 is no longer supported?
yes, but newer versions are not compatible with my hardware on this laptop. Already tested Ubuntu 13.04

> 
If that is not an option have a look at the Lubuntu 12.04 deriviative LXLE

I just did this and the problem persists. I'm writing from LXLE 12.04 LTS.


> 
You could even try a later kernel in your current Lubuntu12.04; search for 3.5.0- or 3.8.0- kernels in synaptic and install the appropriate one to see if it helps out.
ok, will try this and let's see ...

---

