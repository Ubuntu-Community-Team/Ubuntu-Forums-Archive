---
title: "TF2 Not displaying anything when opened."
date: 2013-01-01
forum: Gaming &amp; Leisure
---

### Post by Darksthour on 2013-01-01
So I installed steam and TF2 the other day on my 12.10 and whenever I try to open it there's sound but no video. I installed the drivers according to the sticky in this forum however it doesn't seem to work. Is this because I'm on 12.10 and I should downgrade to 12.04 or did something go amiss with my drivers? I'm new to linux so any help would be greatly appreciated. I'm also running Intel ironlake mobile graphics.

---

### Post by sffvba[e0rt on 2013-01-01
Which sticky (and thus what driver) and what hardware do you have?


404

---

### Post by Darksthour on 2013-01-01
I have a Toshiba satellite a665 with Mobile Intel HM55 Express Chipset. I'm not sure exactly which drivers i'm running I did the install from [http://ubuntuxtreme.com/howto/how-to...ideo-problems/](http://ubuntuxtreme.com/howto/how-to...ideo-problems/)

---

### Post by sffvba[e0rt on 2013-01-01
Just read through several threads and they all point to an issue with Intel and the version of openGL it supports. (In Windows TF2 uses directx and thus may work with your setup but in Linux it uses openGL).

For reference - [http://steamcommunity.com/app/221410/discussions/0/846938351032713908/](http://steamcommunity.com/app/221410/discussions/0/846938351032713908/)

[https://github.com/ValveSoftware/steam-for-linux/issues/19](https://github.com/ValveSoftware/steam-for-linux/issues/19)



404

---

### Post by Darksthour on 2013-01-01
Well it seems this is an issue with intel hatin' on linux.

[http://communities.intel.com/thread/33333](http://communities.intel.com/thread/33333)

and what Frank from steam said:

[http://steamcommunity.com/app/221410/discussions/1/882965118606133134/?tscn=1355530489#c846939854098355972](http://steamcommunity.com/app/221410/discussions/1/882965118606133134/?tscn=1355530489#c846939854098355972)

So I guess until Intel says something or someone gets opengl to work on older Intel chipsets no dice on this working. Or when steam leaves beta it will find more support.

---

### Post by sffvba[e0rt on 2013-01-01
> **Darksthour said:**
> Or when steam leaves beta it will find more support.

We can only hope...


404

---

### Post by Darksthour on 2013-01-01
> **Darksthour said:**
> So I installed steam and TF2 the other day on my 12.10 and whenever I try to open it there's sound but no video. I installed the drivers according to the sticky in this forum however it doesn't seem to work. Is this because I'm on 12.10 and I should downgrade to 12.04 or did something go amiss with my drivers? I'm new to linux so any help would be greatly appreciated. I'm also running Intel ironlake mobile graphics.

> **not found said:**
> We can only hope...


404

Haha. Hey man just wanted to say thanks for the help. Would have been searching for driver updates all day without those links.

---

