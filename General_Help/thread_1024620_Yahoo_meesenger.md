---
title: "Yahoo meesenger"
date: 2008-12-29
forum: General Help
---

### Post by DougieFresh4U on 2008-12-29
Is there a yahoo messenger version for linux? I would like to use my Logitech cam with my friends that have yahoo

---

### Post by BatsotO on 2008-12-29
Use kopete or gyache. Ym version for linux doesn't support video.

---

### Post by DougieFresh4U on 2008-12-29
I have done some reading (wiki) on kopetebut still don't quite understand. Said I needed libjasper, so I installed that also said I needed a couple of other packages but didn't see them in Synaptic. 
Any body know where to get the driver for Logitech as the wiki showed links for other brands of webcam but not Logitech
Thanks
Also gyache has dependency issues

---

### Post by BatsotO on 2008-12-29
Most logitch natively supported i use one too. And i recall kopete need libjasper-runtime and i believe that's in synaptic. Kopete is KDE default, so i think all it needs are in the repo. 
If you have other accounts in you machine be sure to add them in the video line in /etc/group.

---

### Post by DougieFresh4U on 2008-12-29
> **BatsotO said:**
> Most logitch natively supported i use one too. And i recall kopete need libjasper-runtime and i believe that's in synaptic. Kopete is KDE default, so i think all it needs are in the repo. 
If you have other accounts in you machine be sure to add them in the video line in /etc/group.

Thanks for your input.
I installed kopete and libjasper-runtime.. but still seem to have no luck.Am I missing some thing(driver)?

---

### Post by BatsotO on 2008-12-29
Is it run with camorama? If i'm not mistaken you can use envy to install webcam driver.
And can you discribe how it doesn't work.  Does configure --> devices doesn't show anything?

---

### Post by DougieFresh4U on 2008-12-30
> **BatsotO said:**
> Is it run with camorama? If i'm not mistaken you can use envy to install webcam driver.
And can you discribe how it doesn't work.  Does configure --> devices doesn't show anything?

Hi , and thanks.
got it working with 'GyachE'. Was so simple. But my cam is very dark, as either not enough lite in my room or it's something else. But needless to say, I can see others cams very clear. I gave up on Kopete as couldn't get cam working there.

---

