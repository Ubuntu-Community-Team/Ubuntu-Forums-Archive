---
title: "Dash on Ubuntu 12.10 is painfully slow"
date: 2012-11-12
forum: Desktop Environments
---

### Post by tomdkat on 2012-11-12
A few days ago, I upgraded from Ubuntu 12.04 to 12.10 and the upgrade went smoothly.  My system is stable and runs well with the exception of Dash.

Dash takes FOREVER to load icons and when I try to switch filters, say from "System" to "Internet", it seems Dash doesn't really respond.

I'm running Ubuntu 12.10 64-bit on an eMachines system with an AMD Athlon64 3200+ CPU running at 2GHz and with 2.5GB of RAM. I'm running Unity.

Any ideas on how I can find out why Dash is running so poorly?  According to "top", Xorg consistently takes 30%+ of CPU and the other applications I have running are Google Chrome (5 tabs open, one of which is streaming from Pandora via Flash), Mozilla Thunderbird, Empathy (one chat session open), and rdesktop (connected to a Windows XP system).

Thanks!

Peace...

---

### Post by FernandoLB on 2012-11-15
Similar problem. Still unsolved:
[http://ubuntuforums.org/showthread.php?t=2079672](http://ubuntuforums.org/showthread.php?t=2079672)

---

### Post by theeo on 2012-11-22
So this reinstall works for me immediately!
```
sudo apt-get install --reinstall xserver-xorg-video-intel
```

Try dash at Guest account. If it's faster try to reinstall than you should achieve similar response like on guest account. At least it helped for me. 3-4 secs to open Dash and 2 to close (before reinstall about 10sec) however on guest account it's still better 1.5 vs 0.5 sec,  (graphics Intel on i915 driver)

---

### Post by frotzed on 2013-01-01
> **theeo said:**
> So this reinstall works for me immediately!
```
sudo apt-get install --reinstall xserver-xorg-video-intel
```

Try dash at Guest account. If it's faster try to reinstall than you should achieve similar response like on guest account. At least it helped for me. 3-4 secs to open Dash and 2 to close (before reinstall about 10sec) however on guest account it's still better 1.5 vs 0.5 sec,  (graphics Intel on i915 driver)

I confirm this worked for me in resolving the issue of the Dash lagging and generally being very slow.

---

### Post by manishk on 2013-01-17
Just confirming that reinstalling did speed up Dash's launch.

I have an ATI card, so used the following instead.

```
sudo apt-get install --reinstall xserver-xorg-video-**ati**
```

Dash is faster, but not fast...would be thrilled if someone would suggest something that would speed up the searches and overall response.

---

