---
title: "Same old question- Is 64 bit ubuntu worth installing for regular desktops"
date: 2009-06-16
forum: General Help
---

### Post by joy83 on 2009-06-16
Well, I know this has been answered before but just wanted to know if I should install a 64 bit ubuntu 9.04 or the 32 bit on my desktop. My desktop has a 64 bit processor and pretty good. 

Thing is I dont want to install 64 bit if I end up with a lot more headache in installing packages and getting support, since I have heard that 64 bit tends to have less support than 32 bit packages.

My desktop has a Intel Quad Core processor, 8 gig RAM. Will the increase in speed with a 64 bit OS be noticeably different?

---

### Post by merlinus on 2009-06-16
32-bit will not use anywhere that amount of ram, for starters.  I have had no probelsm with 64-bit on a core duo with 4G ram.  I had to find a 64-bit version of skype, but that was the only difficulty in terms of apps.

---

### Post by Hobgoblin on 2009-06-16
I have the 64bit version (after abandoning it in an earlier version of Unbuntu) and have had no problems installing the usual desktop stuff (flash, codecs, java, etc.)

---

### Post by lamego on 2009-06-16
A lot of 32 bits closed source applications like skype can be used using the ia32-libs packages, it provides 32bits versions for the most common libraries.

---

### Post by Cheesemill on 2009-06-16
Same old answers:
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by nolliecrooked on 2009-06-16
kinda, but not if ya wanna have the straight forwardness of 32Bit.

---

### Post by days_of_ruin on 2009-06-16
> **joy83 said:**
> Well, I know this has been answered before but just wanted to know if I should install a 64 bit ubuntu 9.04 or the 32 bit on my desktop. My desktop has a 64 bit processor and pretty good. 

Thing is I dont want to install 64 bit if I end up with a lot more headache in installing packages and getting support, since I have heard that 64 bit tends to have less support than 32 bit packages.

My desktop has a Intel Quad Core processor, **8 gig RAM**. Will the increase in speed with a 64 bit OS be noticeably different?

You aren't even using half of that with 32 bit. You have to use 64 bit to even use more than 4gb of ram.

---

### Post by Cheesemill on 2009-06-16
> **days_of_ruin said:**
> You aren't even using half of that with 32 bit. You have to use 64 bit to even use more than 4gb of ram.

Not strictly true, you can enable PAE in the 32-bit kernel to address more than 4GB.

---

### Post by lukeiamyourfather on 2009-06-16
> **Cheesemill said:**
> Not strictly true, you can enable PAE in the 32-bit kernel to address more than 4GB.

But applications are still limited to 4GB. Not a big deal, but I think PAE would cause more issues than 64-bit. I'd just install 64-bit. Cheers!

---

### Post by celem on 2009-06-16
Having always run 32-bit in the past, due the same concerns as your's, I loaded 64-amd and never looked back. If there is anything that I can't run on 64 bit 9.04, I haven't found it. Load the 64 bit version, which will use all of your memory.

---

