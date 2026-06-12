---
title: "stata 64 bit in ubuntu"
date: 2009-01-29
forum: Education &amp; Science
---

### Post by gatorbrit on 2009-01-29
Hi all, I am considering purchasing the linux version of 64 bit stata to run on 64 bit ubuntu .

The reason is that I need to be able to access all 4GB of my on board ram.  Currently, in 32 bit windows XP I can only get about 1.4 GB of ram to stata.   This is a know and well documented issue of windows memory management.

So my question is whether anyone else has had success with the 64 bit linux flavor of stata and how much memory they can allocate in the..

```
set memory 
```
command

Thanks.  And please don't suggest using R.  As far as I know there isn't an R package for a system GMM estimator using the Bond and Blundell method.

Cheers

Richard

---

### Post by hubie on 2009-01-30
> **gatorbrit said:**
> 
Thanks.  And please don't suggest using R.  As far as I know there isn't an R package for a system GMM estimator using the Bond and Blundell method.


I won't suggest using R, but the [plm]("http://cran.r-project.org/web/packages/plm/plm.pdf") package does appear to do Blundell Bond with the pgmm package (with transformation="ld").

As for your real question, I can't really help since I don't use stata, but their [help page]("http://www.stata.com/help.cgi?flavors") suggests that you are only limited by your system memory.  I know from experience that we've used very large memory spaces on 64-bit linux running IDL/Envi, though we weren't quantifying the amount so I can't give you a good number off the top of my head, but that was the reason we were running it on linux (for the record, it was an 8-processor board with 32 GB RAM).

---

### Post by gatorbrit on 2009-01-30
Thanks!

> **hubie said:**
> I won't suggest using R, but the [plm]("http://cran.r-project.org/web/packages/plm/plm.pdf") package does appear to do Blundell Bond with the pgmm package (with transformation="ld").
.


I stand corrected.  Now my decision is whether I want to spend $400 on stata or get R, but invest in learning the new software....

---

### Post by jbauchet on 2009-01-30
Richard, 

I can't speak about Ubuntu because I haven't tried it, but I recently ran Stata 64-bit on a 64-bit Windows Vista computer with 16G of RAM, and I could get up to 59G of memory in Stata with the set memory command (quite outreageous, actually...).

Stata says that you're limited only by the amount of memory that your computer has, and this seems to indicate that it's really the case. I hope it's similar in Linux; this is the best info I can give.

Good luck.

---

### Post by gatorbrit on 2009-01-30
Thats really great - sounds like stata is also hitting the swap file.   I went ahead and ordered the 64 bit version.  I'll see how it goes.  

I thought of messing with R, but decided I didn't want to spend the time learning a new language when stata does all that I need.

---

### Post by affl1cted on 2009-01-31
Any 64bit operating system can handle memory in quantaties beyond a Terabyte. The change from 32bit to 64bit is not just 2x 32bit, theres billions of billions more accessable memory space.

---

### Post by gatorbrit on 2009-02-05
I got 64 bit stata up and running and it is great - loads of memory.  I'm back to crunchin numbers...:)

---

