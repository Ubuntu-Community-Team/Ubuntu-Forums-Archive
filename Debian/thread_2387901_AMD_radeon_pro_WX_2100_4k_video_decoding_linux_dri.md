---
title: "AMD radeon pro WX 2100 4k video decoding linux driver support"
date: 2018-03-25
forum: Debian
---

### Post by donarntz on 2018-03-25
Hi All,

I'm nursing along my aging AMD system (10 years knock on wood).  I install a firepro w2100 last last year, but I guess due to me not practicing due diligence I discovered it does not decode 4k video.  I've been reading up on the [radeon pro wx 2100]("https://pro.radeon.com/en/product/wx-series/radeon-pro-wx-2100/") and I "think" it supports 4k decoding?  I would like to be able to watch 4k video on my system.  What is the current state of AMD driver support in linux for this to work?

Thanks for any input.

---

### Post by Yellow Pasque on 2018-03-25
Start by looking at the video decode capabilities. What video player are you trying to use and what video output method?
```
sudo apt-get install vdpauinfo vainfo
vdpauinfo
vainfo
```

EDIT: I believe the card itself is capable if it's using UVD 6.x

---

### Post by donarntz on 2018-03-25
I'm actually looking to stream from youtube, netflix etc.

[https://paste.ubuntu.com/p/BKVCbc76bg/](https://paste.ubuntu.com/p/BKVCbc76bg/)

---

### Post by Yellow Pasque on 2018-03-25
In Linux, hardware accelerated decode inside the browser is painful. I think Firefox gave up, and every now and then, I hear something about Chrome/ium experiment: [https://chromium-review.googlesource.com/c/chromium/src/+/532294](https://chromium-review.googlesource.com/c/chromium/src/+/532294)

I'm kind of surprised that VDPAU doesn't report any HEVC support. What version of Ubuntu are you using?

---

### Post by donarntz on 2018-03-25
I think I marked my post incorrectly, as I'm using Debian testing.  I used Ubuntu for years.  I guess old habits die hard.

---

### Post by wildmanne39 on 2018-03-25
*Thread moved to **Debian, a more appropriate forum**.*

---

