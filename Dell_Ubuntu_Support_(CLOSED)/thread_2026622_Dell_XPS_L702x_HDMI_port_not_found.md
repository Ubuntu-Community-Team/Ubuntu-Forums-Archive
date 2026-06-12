---
title: "Dell XPS L702x HDMI port not found"
date: 2012-07-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by KaisaUbun2 on 2012-07-15
So I just installed bumblebee which finally enabled ubuntu to see my graphic card, if now there was only a solution for the HDMI for my TV any ideas?????

---

### Post by SigmaSanti on 2012-07-18
You can buy a mini-displayport to hdmi converter, this will work in ubuntu because it relies on the intel card instead of the nvidia. (This works on my Dell l502x)
I don't know if dell's displayport supports audio though.

---

### Post by KaisaUbun2 on 2012-07-20
> **SigmaSanti said:**
> You can buy a mini-displayport to hdmi converter, this will work in ubuntu because it relies on the intel card instead of the nvidia. (This works on my Dell l502x)
I don't know if dell's displayport supports audio though.

it does, but i'd rather not buy anything, I guess I will just wait until bumblebee comes out with a fix, in the mean time I will just run windows 7 whenever i want to watch something with an hdmi cable

---

### Post by SigmaSanti on 2012-07-20
Mini-display port to hdmi is usually pretty cheap, $10 - $20 USD.
Anyhow there are two nvidia graphics drivers nouveau nvidia, and propriatery  nvidia - open vs closed source.
Bumblebee supports both but installs nouveau by default. Instructions for installing the other nvidia driver should be on the bumblebee wiki. The propriety nvidia driver has a configuration tool that allows you to select the display. This might work.

---

