---
title: "Dimension E520 N"
date: 2007-06-07
forum: Dell  Ubuntu Support
---

### Post by luckyd on 2007-06-07
Is the lower end Dimension E520 N with Ubuntu feisty preinstalled fast enough to run Beryl? Does anyone have this setup that can recommend it to me?

---

### Post by mifi on 2007-06-08
> **luckyd said:**
> Is the lower end Dimension E520 N with Ubuntu feisty preinstalled fast enough to run Beryl? Does anyone have this setup that can recommend it to me?I am using it with Compiz with no problems. That includes all the fancy movements. 
But I have upgraded to the nVidia 7300 graphics card and I have not tried Beryl. Beryl should be roughly the same as Compiz tho.

m

---

### Post by PriceChild on 2007-06-08
All the Dells come with either intel or nvidia depending on how good performance you want.

Both are perfect for Beryl/Compiz although you will see better performance out of the nvidia.

---

### Post by luckyd on 2007-06-08
Will extremly memory consuming effects like rain work well?

---

### Post by ScottLij on 2007-06-08
I've got Compiz working on my E520N and it's very cool.  I was just wondering if theres a way to rotate the screen 90 degrees?

---

### Post by benanzo on 2007-06-08
Though I have not any benchmarks to prove it, it seems to me that the Intel GMA950 performs  just as good or better with Beryl than nVidia.  I am chocking this up to the Free Intel drivers.  A couple of the more GPU-intensive tasks like Rain+Cube simultaneously perform better with nVidia -- but as a whole, it feels like the Intel drivers are more finely-tuned and stable.

I just got hold of a mainboard with the newest Intel X3000 G965 graphics - whoa.  I see better performance than even the nVidia while running several of the GPU intensive plugins at the same time like Rain+Cube+Snow all while playing a fullscreen DVD (I'm trying to get it to crash which has been tough so far.)

So, any later Intel graphics GMA950/G965 will handle Beryl very well.

---

### Post by PriceChild on 2007-06-08
> **luckyd said:**
> Will extremly memory consuming effects like rain work well?Rain isn't really about memory. It needs pixel shaders to be any good which afaik the 950 has... someone correct me if I'm wong :)

---

### Post by luckyd on 2007-06-10
If the GMA 950 is just as good, then why does the Nividia cost more?

---

### Post by bur[n]er on 2007-06-11
Got me on the price.  I assume the nvidia is even better, but I have the onboard intel and it works with beryl wonderfully.  Animated skydomes, wobbly and flaming windows, and all other beryl goodness works well.

---

### Post by benanzo on 2007-06-11
The nVidia cards have significantly more power than any of the Intel chips.  That is why you pay a premium for them.  However, because their drivers are not developed openly, I find that Intel's chips perform the same or better.  If we could get solid 3D drivers for their chips into Xorg, there is no doubt in my mind that they would blow Intel's offerings away.  But as of now their drivers are inferior.

---

### Post by luckyd on 2007-06-11
Since I ordered my dell with the nVidia card, will I see at least good beryl preformance? I hope it will, because I had to pay $50 more for it and beryl is the main reason why I bought a new computer, with what I thought was a good video card..

---

### Post by benanzo on 2007-06-12
You'll see great Beryl performance.  As good as it can be.  The issue between the Intel and nVidia chips is minor.  I find that the Intel chips (which are much less capable) actually perform as well as nVidia purely because they have better drivers.  nVidia performs well, don't get me wrong.  But they could perform much better.

---

### Post by drfox on 2007-06-25
I can't get Beryl, Compiz, or Compiz fusion to work with my E520. The problem appears to be the Intel 82G965 card.

I had Beryl running on my Dell Dimension 2400 with its integrated Intel video, and it's running fine on my Toshiba A105 laptop, again with integrated Intel.

My guess is that the Intel driver isn't working right with the 965 card, but I'm not enough of a gearhead to figure out the exact issue.  Is there anyone who has had success with a E520 with the Intel graphics?

Larry

---

### Post by bluemech on 2007-06-28
> **drfox said:**
> I can't get Beryl, Compiz, or Compiz fusion to work with my E520. The problem appears to be the Intel 82G965 card.

I had Beryl running on my Dell Dimension 2400 with its integrated Intel video, and it's running fine on my Toshiba A105 laptop, again with integrated Intel.

My guess is that the Intel driver isn't working right with the 965 card, but I'm not enough of a gearhead to figure out the exact issue.  Is there anyone who has had success with a E520 with the Intel graphics?

Larry

I have this exact same card, and this exact same problem. What's more, I'm running the 64-bit version of Feisty. Anyone have any answers?

---

### Post by lahook on 2007-06-28
There is a new driver for the intel 965 but it hasn't been compiled for Ubuntu yet. I don't know enough about compiling to try it. I'm afraid if I try to I'll break something else. Here's the link: [http://www.intellinuxgraphics.org/](http://www.intellinuxgraphics.org/)

---

