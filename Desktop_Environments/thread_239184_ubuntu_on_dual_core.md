---
title: "ubuntu on dual core?"
date: 2006-08-18
forum: Desktop Environments
---

### Post by m.musashi on 2006-08-18
I currently have dapper on my desktop running an athlon 64. With prices dropping like crazy I was thinking of picking up an athlong 64 x2 (dual core jobs) and upgrading. If I just drop the new dual core processor in my current setup, would I need to change anything or reinstall? Does dual core present any problems for ubuntu or linux?

Sorry for the rather noob questions but I still don't know it all (or even a fraction there of:)). Can one of you enlighten me?

Thanks.

---

### Post by Fass on 2006-08-18
IIRC, you're going to have to install an SMP kernel if the one you have now doesn't have support for it.

---

### Post by m.musashi on 2006-08-18
Thanks for the info.

Do yo know how I would know that? I only installed the stock ubuntu 6.06 for 32 bit x86.

---

### Post by Fass on 2006-08-18
```
uname -a
```

If the output contains "SMP" you're set.

---

### Post by m.musashi on 2006-08-19
Nope. No SMP
```
Linux number 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux
```
Of course I'm still running a single core. When I install the new processor, do you think I should reinstall ubuntu or just apt-get the SMP kernel? Would a reinstall automatically use an SMP kernel or would I still need to apt-get it anyway?

Thanks again.

---

### Post by patrickfromspain on 2006-08-19
just apt-get it.. reinstall won't install a SMP enabled kernel.

---

### Post by 5-HT on 2006-08-19
> **m.musashi said:**
> Nope. No SMP...Of course I'm still running a single core. When I install the new processor, do you think I should reinstall ubuntu or just apt-get the SMP kernel? Would a reinstall automatically use an SMP kernel or would I still need to apt-get it anyway?

Thanks again.

No need to reinstall, just grab the relevant SMP kernel  once you're running on the new processor. You'd still get the 386 kernel if you reinstall via CD- though I believe that may not be the case if using the DVD.

HTH

---

### Post by m.musashi on 2006-08-19
Thanks for all the info. I think I understand.

5-HT...there's an ubuntu DVD? I'd better look into this.

---

