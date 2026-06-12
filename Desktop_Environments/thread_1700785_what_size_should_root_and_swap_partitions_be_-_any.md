---
title: "what size should /root and swap partitions be - any problem over-estimating?"
date: 2011-03-05
forum: Desktop Environments
---

### Post by nrundy on 2011-03-05
When setting up a new install of Ubuntu with separate partitions for /root, /home, and swap, how big should one make the /root and swap partitions?

I've seen estimates that swap should be 1.3 - 2 times the amount of Ram. And I've seen estimates that /root should be 5 - 25GB in size.

Is there any harm/disadvantage in over-estimating the space allocated for these partitions? If I give /root and swap more space than they really need will this have any negative side effects? I'll have way more HDD space than I'll ever use for /Home either way.

---

### Post by egglestn on 2011-03-05
Short answer is that if you make your swap 2X your RAM and your root in the order you mention you will have space to spare. The only time there is problems is if you are using older hardware and there is a shortage of disk space...if you are sure you have enough then more is better..
As with life its all about a compromise between what is possible and what is ideal

---

### Post by ShakeyJake on 2011-03-05
Well I'm currently using 6.18GiB of my 29.3GiB /root SSD and none of my 8GiB swap. 

I think you'd be fine with 20GiB at most for /root and just use slightly more swap than you have RAM.(My 8_GiB_ swap is slightly more than my 8_GB_ RAM)

---

