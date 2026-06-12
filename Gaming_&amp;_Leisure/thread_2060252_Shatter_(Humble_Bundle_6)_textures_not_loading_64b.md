---
title: "Shatter (Humble Bundle 6) textures not loading 64bit Ubuntu"
date: 2012-09-19
forum: Gaming &amp; Leisure
---

### Post by nfarley88 on 2012-09-19
Hi,
Recently got Shatter in the humble bundle 6, but for some reason the textures aren't loading properly? I did read in the installation on another machine (Fedora) that it relies on 32 bit libraries, but I don't know which to install if that's what's needed. I run the open source amd drivers. 

It's a real shame as it makes the game pretty much unplayable! Has anyone fixed this problem on their 64 bit Ubuntu? Or have any suggestions?

Thanks in advance

---

### Post by fixles on 2012-09-19
Sorry I'm not sure... I cant get through the install... I'm on 64bit too but its saying missing Core X11 Libraries libXft.so.2.  Did you have this problem?

---

### Post by cgolson84 on 2012-09-19
My guess is that it's your drivers.  I'm using proprietary Nvidia drivers and I played it for an hour or so today with no issue.  Installed Shatter via the Software Center in Kubuntu 12.04

---

### Post by Sealbhach on 2012-09-19
I'm on 64bit Kubuntu and it's running fine, just to confirm that it does work.  Make sure you have ia32-libs installed (I think that's what the warning was about in the setup script).

.

---

### Post by hanjHH on 2012-09-21
> **cgolson84 said:**
> My guess is that it's your drivers.  I'm using proprietary Nvidia drivers and I played it for an hour or so today with no issue.  Installed Shatter via the Software Center in Kubuntu 12.04

 Thank you. I was having the same problems as the OP. Activating the proprietary ATI/AMD-drivers solved it for me. Thanks, now I can enjoy all the addictive goodness that is Shatter.

---

### Post by Ginz on 2012-09-23
I had the same Problem on 32bit Ubuntu 12.04 with Intel Graphics GM45. Try:

```
export force_s3tc_enable=true
```

Solved the problem for me anyway. (Also worked with Swords and Soldiers in a previous Humble Bundle)

---

### Post by nfarley88 on 2012-09-24
> **Ginz said:**
> I had the same Problem on 32bit Ubuntu 12.04 with Intel Graphics GM45. Try:

```
export force_s3tc_enable=true
```
Yes! This fixed the problem (proprietary drivers don't work with my APU).

---

