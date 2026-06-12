---
title: "How do I install nVidia drivers on a custom 2.6.18 SMP kernel?"
date: 2006-10-04
forum: Desktop Environments
---

### Post by sedgie on 2006-10-04
I'm new to linux, but I noticed that I didn't have an SMP kernel. I have an Athlon 64 X2 3800+.

I downloaded 2.6.18 source from kernel.org, compiled with SMP on K8, and mkinitrd'd. 

Now, I have a 7800GT and I have no idea how to go about installing the Nvidia drivers. I think I have to compile a kernel module, but I don't know how to do that given my custom kernel. Could someone fully walk me through this? Thanks.

---

### Post by hanzomon4 on 2006-10-05
Check this guided out I used it for my custom kernels [Latest Nvidia Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

I had to use Method two

---

### Post by sedgie on 2006-10-05
I'm going to try that this afternoon. I'll let you know how it went. I assume I'll have to use Method 2 as well.

---

### Post by dannyboy79 on 2006-10-05
sedgie, there was no reason to compile a new kernel just for smp, all you had to do was go to synaptic and download that kernel. check out this link, [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

### Post by sedgie on 2006-10-05
I wanted to have 2.6.18 AND K8.

That worked hanzo, I had to make a few adjustments but wow, it's running like butter. Thanks!

---

### Post by sedgie on 2006-10-06
Hmmm... is it worth it to have compiled with K8 and 2.6.18? Is the advantage sizable? I may just wait until Ubuntu releases it in their repos; when will that be?

---

### Post by sedgie on 2006-10-06
Bump...

---

