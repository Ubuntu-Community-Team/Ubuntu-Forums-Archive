---
title: "Unity GUI hangs randomly. Often with Chromium. 12.04"
date: 2013-08-28
forum: Desktop Environments
---

### Post by nleo2 on 2013-08-28
Unity hangs periodicali for me.

Sometimes I can't even switch to text terminal (<Ctrl><Alt><F1>)

Sometimes, current window still active, but there is no panels and I can't swich to others window. When I can switch to text terminal and kill X server.

I noticed that if I run Chrome or Chromium - 100% after time there will be problems with DE.

 Any thoughts? What logs can I see or something? Or go to KDE or XFCE?

---

### Post by lah7 on 2013-08-29
Welcome to the community! If your entire system is locking up like that, you could be running low on memory, swap space or system resources (RAM/CPU).

**Please could you post the specs of your computer so we can get a better insight?** *(mainly CPU/RAM/Swap/GPU)*

You may wish to open and keep a check on the **System Monitor** to see if the system becomes overloaded very quickly whilst you're doing your activities.

Alternately, this could be a graphics problem, are you using any proprietary drivers?

If it helps, you may wish to use a more lightweight desktop environment instead, like LXDE, XFCE or Gnome Classic since Unity might not be up to speed with your graphics processor.

---

### Post by redtailedhawk on 2013-08-30
Chrome itself can be resource hungry but some of the extensions are even more so. I had Chrome using 100% of one of my CPUs, the other 3 were normal then that one would go down to normal and another one would go up to 100% and then move to another one the same way.I went to 'Tools' and started to delete extensions, after the first one the CPU usage returned to normal, I can't remember the name of the extension but it was supposed to make chrome faster. I continued to delete the extensions I didn't need or use and Chrome is running great now.If you have an extension like that I suggest you delete it and any that you don't need or really use and also limit the number of tabs you have open.Hope this helps.

---

### Post by nleo2 on 2013-09-01
Thanks for answers.

ASUS Zenbook UX21A, Intel Core i7 3517U, 1.9GGh, 4Gb, 256Gb SSD, Intel HD Graphics 4000 Ubuntu 32 bit

I never user Chrome activly and there is often scenario like thise:

1) Open Chrome, do some stuff
2) Close Chrome
3) Do some random stuff
4) *OPTINAL* Take system to sleep.
5) *OPTINAL* Wake up. 
6) Do some random stuff
7) Unity hangs. PROFIT :(

---

### Post by lah7 on 2013-09-01
From your specs, it definitely can't be low resources, since they all exceed the minimum/recommended requirements.

As far as I'm aware, there is no need for proprietary drivers for Intel graphics so drivers may not be the issue here.

I believe Unity does use hardware acceleration, but since your graphics are integrated with the CPU, it may take out a bit of work by trying a different desktop environment for a while. Like you say, XFCE or KDE are alternates. LXDE is even more lightweight. If you was to try this and find your system hanging again, it's likely to be another application crashing the system or an incompatible package somewhere.

I wish I knew, but I don't where exactly where Unity logs are stored, but you can view debug output from the terminal (or CTRL+ALT+F1) and typing 'unity' *(this restarts Unity, do not close/logout the terminal unless you want to terminate Unity)*

---

### Post by hg-knight on 2013-09-01
have you tried another browser to see if the same thing happens.
I use chrome on an old netbook with no issues.

A wild guess, but remove 1 stick of ram at a time to see if this helps.
Had similar on a desktop and found  of 2 sticks of ram was faulty
other than that your system should cruise along nicely with those specs

---

### Post by nleo2 on 2013-09-06
I use Opera. Usially no problems.

 Today click on previosly opened tab and comp turned off. At one moment. But there was uptime about few days and several suspends to RAM.

---

