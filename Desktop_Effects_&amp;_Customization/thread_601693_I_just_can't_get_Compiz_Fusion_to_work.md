---
title: "I just can't get Compiz Fusion to work"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by evilmnky204 on 2007-11-03
I tried all guides, and I even installed the new ATI drivers but Compiz just won't work. I have an ATI x1650 Pro and it just won't work :\

I installed the extra Compiz manager, and even then it won't work. I'm using Ubuntu 7.10 and when I select normal, or extra in the Visual Effects, and it says "This Composite Extension is not available" Anybody here have the same card and managed to get it to work?

---

### Post by carlosjuero on 2007-11-03
> **evilmnky204 said:**
> I tried all guides, and I even installed the new ATI drivers but Compiz just won't work. I have an ATI x1650 Pro and it just won't work :\

I installed the extra Compiz manager, and even then it won't work. I'm using Ubuntu 7.10 and when I select normal, or extra in the Visual Effects, and it says "This Composite Extension is not available" Anybody here have the same card and managed to get it to work?
You need to install the xgl X server most likely

```

apt-get install xserver-xgl

```

Until I install that on my machine (ATI X1650) the composite doesn't work. The only way the fglrx drivers will work with Compiz is with the xgl server.

---

### Post by Zorael on 2007-11-03
Related to [http://ubuntuforums.org/showthread.php?t=569654](http://ubuntuforums.org/showthread.php?t=569654) ?

---

