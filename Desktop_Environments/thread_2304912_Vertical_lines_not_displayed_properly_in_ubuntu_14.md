---
title: "Vertical lines not displayed properly in ubuntu 14.04 on HP 23-r012il"
date: 2015-12-01
forum: Desktop Environments
---

### Post by manojtripathi2008 on 2015-12-01
Dear forum members,

My display doesn't show the vertical lines properly. It seems as if the rows of pixels are staggered/shifted by one pixel alternatively. In simple terms, it creates a zipper like pattern out of perfectly vertical lines. 

In contrast to this, the horizontal lines are perfectly fine. This would not have bothered me, but the text suffers the most from this nuisance, as you can see in the attached image. 

An interesting thing about this is that when I take a screenshot (print screen), the resulting image looks perfect (without staggered pixels). That is why I had to take a photo of my desktop screen with my cellphone. 

Of course I searched the internet, but could not find a similar problem reported by anyone (may be I am not searching with the right keywords). However, what I found was that my driver may not be a problem because ubuntu takes care of the Intel HD graphics cards.

It shows that it has **Intel Haswell Desktop** under the **Graphics** field in **Details**. The processor is Core i5-4460T 1.90 GHz.

Please help.
Thanks.

---

### Post by manojtripathi2008 on 2015-12-02
Two more updates:
1. The grub window (the one which asks me to choose from different OS ) is unaffected by this issue.

2. This issue is not there in the recovery mode.

---

### Post by ytwu on 2015-12-20
> **manojtripathi2008 said:**
> Dear forum members,

My display doesn't show the vertical lines properly. It seems as if the rows of pixels are staggered/shifted by one pixel alternatively. In simple terms, it creates a zipper like pattern out of perfectly vertical lines. 

In contrast to this, the horizontal lines are perfectly fine. This would not have bothered me, but the text suffers the most from this nuisance, as you can see in the attached image. 

An interesting thing about this is that when I take a screenshot (print screen), the resulting image looks perfect (without staggered pixels). That is why I had to take a photo of my desktop screen with my cellphone. 

Of course I searched the internet, but could not find a similar problem reported by anyone (may be I am not searching with the right keywords). However, what I found was that my driver may not be a problem because ubuntu takes care of the Intel HD graphics cards.

It shows that it has **Intel Haswell Desktop** under the **Graphics** field in **Details**. The processor is Core i5-4460T 1.90 GHz.

Please help.
Thanks.

I got the same problem after upgrade to initrd.img-4.x.x-x and found no solution. However, boot up using old version, initrd.img-3.x.x-x, the problem dispeared.
Still try to look for some solution.

---

