---
title: "Best kernel for my situation?"
date: 2006-10-06
forum: Desktop Environments
---

### Post by Megatog615 on 2006-10-06
I have an AMD Athlon 64, which is of the AMD64 architecture, of course. I don't want to run 64-bit just yet, due to the lack of software support for now. I'm a gamer, and games such as Tremulous don't run in 64-bit very well, and Adobe Flash doesn't run in 64-bit at all, without a lot of work involved.

I am running a 386 kernel, for full compatability(practically everything can run on a 386 kernel, I've come to realize). Is there a 32-bit kernel for AMD64 that can give me a performance boost?

Should I just go 64-bit and make the 32-bit only applications run in 32-bit mode? I've heard you can do this, through [Wikipedia](http://en.wikipedia.org/wiki/Amd64#Linux). Am I reading it wrong?

---

### Post by Magnes on 2006-10-06
Well, on Dapper install kernel k7, on Edgy generic. I use k7 (on 32bit Athlon) and have no problems with it.

---

### Post by Megatog615 on 2006-10-06
Really? An AMD64, which is K8, works with the K7 kernel? What kinds of performance boosts do you gain from doing that? Or do you know of any?

---

### Post by madmetal on 2006-10-06
i also suggest k7 kernel which i use with athlon64.

---

### Post by angkor on 2006-10-06
> **Megatog615 said:**
> Really? An AMD64, which is K8, works with the K7 kernel? What kinds of performance boosts do you gain from doing that? Or do you know of any?

Not much. But the system *feels* faster ;) Also the default kernel didn't recognize over +/- 950MB ram on my machine. (Don't know if that is still the case). The k7 recognized all of my RAM and that is a real performance boost if you have more than that.

---

### Post by Megatog615 on 2006-10-06
Hmm... I do have 1024mb of ram, I'll give it a try. Hey, if it doesn't work, I can just fall back to my ol' 386 kernel.

But, what's this? The k7 kernel was obsoleted by linux-image-2.6.17-10-*generic*? Is there a difference?

---

