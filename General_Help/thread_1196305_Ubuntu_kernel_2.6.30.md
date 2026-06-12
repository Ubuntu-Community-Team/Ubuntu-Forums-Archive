---
title: "Ubuntu kernel 2.6.30"
date: 2009-06-24
forum: General Help
---

### Post by rgrasell on 2009-06-24
Is there a specific ubuntu packaged kernel 2.6.30?
If not, can I use the vanilla kernel?

---

### Post by snowpine on 2009-06-24
Yes, 2.6.30 is in the upcoming Ubuntu 9.10 Karmic Koala.

---

### Post by rgrasell on 2009-06-24
Will it ever be available for 9.04? and when?

---

### Post by Chemical Imbalance on 2009-06-24
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)

---

### Post by snowpine on 2009-06-24
> **rgrasell said:**
> Will it ever be available for 9.04? and when?

9.04 will *always* feature kernel 2.6.28. This is the way Ubuntu works; you never get a major update (like a new kernel) through normal updates. Instead, you upgrade everything at the same time by moving to a new release every 6 months.

That being said, you can install 2.6.30 in jaunty at your own risk by following the link in the post above mine. :)

---

### Post by rgrasell on 2009-06-24
thanks, that's perfect.

edit: wait is there some kind of risk?!

---

### Post by snowpine on 2009-06-24
> **rgrasell said:**
> thanks, that's perfect.

edit: wait is there some kind of risk?!

Jaunty is designed and tested to be stable with kernel 2.6.28. (2.6.30 did not exist at the time Jaunty was released.)

The risk is minimal however, because if there is a problem with the new kernel, you can easily boot back into 2.6.28 from your Grub menu. I recommend you go for it if you're curious. :)

---

### Post by rgrasell on 2009-06-24
ok thanks.  I need the new drm in 2.6.30... so ill go try :)

---

### Post by s3a on 2009-06-24
DRM?? As in what plagues the windows world??

---

### Post by rgrasell on 2009-06-24
lol Direct Rendering Manager i believe

---

