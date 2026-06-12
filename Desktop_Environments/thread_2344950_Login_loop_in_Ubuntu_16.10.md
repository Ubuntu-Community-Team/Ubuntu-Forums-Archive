---
title: "Login loop in Ubuntu 16.10"
date: 2016-11-29
forum: Desktop Environments
---

### Post by tommy2k10 on 2016-11-29
Whenever I try to log in to Ubuntu 16.10, it waits for a minute, I just get the splash screen and then the login screen appears again.  
I did CTRL + ALT + F1, and ran 

```
sudo lshw -C display
```

It is an NVidia GT6150 nForce 430 driver.
I had read on these forums, that to recitfy the problem, uninstall it, so I did:

```
sudo apt purge NVidia*
```

which did the trick.  I got in fine.

This morning I thought I would download the latest NVidia driver manually and seeing if that worked, firstly choosing it from the NVidia drivers page (the latest Version 304.132) and then using the release / version number using this code:

```
sudo apt-get install nvidia-304
```

It told me it was installing, then I rebooted; I got the login loop again.

I repeated the uninstall process, and when Ubuntu boots, I get:

Ubuntu 16.10 has experienced an internal error.  When I click Show Details, I get what is attached.

The system works fine, albeit a bit slow, and sometimes the graphics are a bit fuzzy.

---

### Post by drao4l on 2016-12-02
Hi, I'm new to this forum. This phenomenon also occurred with my lubuntu 16.10 desktop environment upgraded from 16.04 under core-i5 2450 Acer Aspire TimelineX environment with i-915 display driver.
So, this is not restricted to nVidia driver issue. I cannot yet restored my login yet.

---

### Post by oldrocker99 on 2016-12-02
You're usually better off installing a fresh 16.10 rather than upgrading; a **lot** of people have reported problems with upgrading over the years. Try that.

---

### Post by tommy2k10 on 2016-12-02
Thankyou; I will try that and report back.

---

### Post by sledhead45 on 2016-12-17
I had the same problem as OP where I was suddenly stuck in a login loop.

Issuing a:
```
sudo apt purge NVidia*
```
fixed the login loop problem and I'm not yet noticing any video related problems. Any ill side effects of not reinstalling these nvidia packages?

---

