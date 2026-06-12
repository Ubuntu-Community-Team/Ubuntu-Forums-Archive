---
title: "Installation Confirmation : Manual partition"
date: 2009-03-08
forum: General Help
---

### Post by BGFG on 2009-03-08
Hi,
my current setup is separate partitions for /, /home and /swap.
With jaunty, I assume that I can overwrite my existing / with a clean jaunty / and then it will simply boot and find my pre-existing home and swap. 

Am I correct ?

Thanks.

---

### Post by Scar-face on 2009-03-08
as long as you point jaunty to your home and swap partitions during the installations everything will be fine.

---

### Post by BGFG on 2009-03-08
As I thought. Thanks :)

---

### Post by zvacet on 2009-03-08
Keep in mind that Jaunty use ext4 format,so it will be good to change from ext3>ext4.Search forums for that kind of result.

---

### Post by BGFG on 2009-03-09
> **zvacet said:**
> Keep in mind that Jaunty use ext4 format,so it will be good to change from ext3>ext4.Search forums for that kind of result.

Indeed, I forgot to mention that. I will be using ext4 for the file system. I will do some research before i look to convert my other drives though.
A thread on supposed ext4 data loss had me concerned but as it would turn out it is actually existing software not properly optimizing ext4's delayed write capability.
My system is on a ups anyway and I'm also planning a minimal install from which I'll add components as i need them, so I have power outages covered and a 'crash' should be unlikely.

Thanks!

---

