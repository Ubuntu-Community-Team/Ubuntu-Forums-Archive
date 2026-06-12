---
title: "4gb of Ram on Debian?"
date: 2008-08-11
forum: Debian
---

### Post by molom on 2008-08-11
What is the maximum amount of RAM Debian can use on the 32bit edition? I want to use 4gb of Ram at 800mhz. And does it support more?

My motherboard supports the amount and speed.

Cheers,
molom

---

### Post by coffeecat on 2008-08-11
You won't even be able to use the whole 4Gb with a 32-bit OS, whether Linux, Windows or whatever. [Click here for more information]("http://www.dansdata.com/askdan00015.htm").

---

### Post by molom on 2008-08-11
> **coffeecat said:**
> You won't even be able to use the whole 4Gb with a 32-bit OS, whether Linux, Windows or whatever. [Click here for more information]("http://www.dansdata.com/askdan00015.htm").

Thanks for that, that was a really in depth article that I couldn't manage to find.

So, another question. When talking about 64-bit versions, are they limited to AMD64 or can 64bit editions work with Intel Dual/Quad cores as well?

And is it true that 32bit Linux editions ignore quadcore processors and limit them to 2 cores?

---

### Post by kerry_s on 2008-08-11
you can use 4gb on 32bit debian just fine, after the install just grab the big-mem kernel. the big-mem kernel can handle 4->64gb ram. quad cores work fine as well.

---

### Post by werries on 2008-08-11
you would need a 64 bit intel processor. :)

---

### Post by Canis familiaris on 2008-08-11
> **werries said:**
> you would need a 64 bit intel processor. :)

Not nessecary. A 32bit proccy with PAE would suffice.

---

### Post by molom on 2008-08-11
Thanks I think I understand now. You really like minimalism kerry ;)
Anything else that I should know, please post.
Thanks for everything guys! :)

Cheers,
molom

---

### Post by kerry_s on 2008-08-11
> **molom said:**
> Thanks I think I understand now. You really like minimalism kerry ;)
Anything else that I should know, please post.
Thanks for everything guys! :)

Cheers,
molom

yeah, sorry about the large pic, i already had the image uploaded here on the forums and the only way to use it again was to include it in the post, just being lazy. :lolflag:

i'll remove the pic now that you've seen it. :)

---

### Post by basenvironment on 2008-08-11
> **kerry_s said:**
> you can use 4gb on 32bit debian just fine
+1

linux-image-2.6-686-bigmem kernel is what you need

---

