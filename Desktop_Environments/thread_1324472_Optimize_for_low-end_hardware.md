---
title: "Optimize for low-end hardware"
date: 2009-11-12
forum: Desktop Environments
---

### Post by Ephilei on 2009-11-12
The only time I've run Ubuntu has been on low-end systems. I just installed 9.10 on a Pentium 2 with 400MB RAM and am disappointed with the speed. Scrolling and switching apps took >1sec to respond. I've haven't really run Ubuntu in two years. Is this typical now? 

What can I do to optimize? This is to run as a Web kiosk. I've already disabled easy stuff from the startup programs GUI.

Might there be a better distro than Ubuntu for this?

---

### Post by CalvinMorrison on 2009-11-12
Ephilei,

I wouldn't suggest using a full blow desktop environment, Especially gnome.

Even on a pentium 3 gnome is slow. i can't imagine the sluggishness on a old p2.

I'd advise you use Debian *which is almost exactly like ubuntu* and install lxde, a light weight desktop environment

that should speed things up alot.


Calvin Morrison

---

### Post by Ephilei on 2009-11-13
> **CalvinMorrison said:**
> I'd advise you use Debian *which is almost exactly like ubuntu* and install lxde, a light weight desktop environment

Thanks! I'm trying that now.

---

### Post by OneMixDJ on 2009-11-17
> **Ephilei said:**
> Thanks! I'm trying that now.

Keep us posted. :)

---

### Post by Ephilei on 2009-11-23
Installed lxde and it runs very well. Installing Firefox on it is driving me crazy, but it's as fast as I could hope.

---

### Post by snowpine on 2009-11-23
> **Ephilei said:**
> Installed lxde and it runs very well. Installing Firefox on it is driving me crazy, but it's as fast as I could hope.

I'm glad LXDE is working for you!

This will install firefox:

```
sudo apt-get install firefox
```

Good luck.

---

