---
title: "Dell Studio 1555 and microphone"
date: 2009-08-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kamilek on 2009-08-26
Hi!
I am not able to use my microphone, how to adjust my mixer settings to use an external microphone? The microphone is simply mute (at least I can't register any voice).

Also why after every boot I must again adjust all my mixer settings? How to save them?

:-({|=

I use Arch, I had same problems with Ubuntu JJ.

---

### Post by Sam Lars on 2009-08-27
> **kamilek said:**
> Hi!
Also why after every boot I must again adjust all my mixer settings? How to save them?


Try
```
sudo alsactl store 0
```

---

