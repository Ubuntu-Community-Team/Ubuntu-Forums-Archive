---
title: "Swap Space"
date: 2005-04-25
forum: Desktop Environments
---

### Post by Simian on 2005-04-25
I recently submittited infomation about my computer to ubuntu (as you do) and I noticed that I don't have any swap space. I'm sure this is bad as I know that it is supposed to be approx double your RAM. But how bad is it and how do I fix/adjust it?

Thanks.

---

### Post by mirons on 2005-04-25
[QUOTE=Simian] ...I don't have any swap space... But how bad is it and how do I fix/adjust it?

Thanks.[/QUOTE]

I can't say how bad it is: swap is used to store processes that are not active (e.g. waiting for some event) on the hd instead that on RAM. This allow you to have more RAM free at the cost of slower access on that processes. If you have a lot of RAM I think you can live fine also without swap (this is what I do). While if you want to have a swap partition you have to create it through filesystem utils (e.g. tune2fs if you are using ext2/ext3 fs)/parted. Resize a partition, create a new one and format it as swap.

---

### Post by nad on 2005-04-25
Good info.

Just a note: Use parted to create a partition with a type of linux swap. The operating system will automatically configure and set it up upon finding it at startup.

---

### Post by tread on 2005-04-25
Also, if you have this installed on a laptop and want to use the hibernate option you need the swap space.

---

### Post by Simian on 2005-04-25
Thanks for the advice everyone. I have 500MB Ram on my laptop but as I understand it, it isn't necessary to double that for swap. Would you recomend 250MB maybe?

---

### Post by nad on 2005-04-25
It depends on what it will be used for. With a modern machine with 500M ram for example, 200M should be sufficient in order to catch any overflow of typical use. If you are manipulating large graphics images, you may want 1G or more. If you are mounting and manipulating iso images such as knoppix, 3G is not unreasonable.

---

### Post by tread on 2005-04-25
Also, you might need to check hibernate requirements .. if theres 512 mb being used, hibernate might need to write 512mb. Unless you have a major space crunch, I'd stick with the double ram rule.

---

### Post by Simian on 2005-04-25
Ok I see now. Thanks again for the good advice. I will try to sort it out.   :)

---

