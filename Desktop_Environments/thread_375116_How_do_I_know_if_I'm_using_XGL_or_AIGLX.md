---
title: "How do I know if I'm using XGL or AIGLX?"
date: 2007-03-03
forum: Desktop Environments
---

### Post by rainwalker on 2007-03-03
I installed Beryl successfully by using the guide at [https://help.ubuntu.com/community/BerylOnEdgy](https://help.ubuntu.com/community/BerylOnEdgy) and things are working fine, but I don't know how to tell if I'm using XGL or AIGLX. The "Rendering" settings are all set to Automatic, and I'm using a " VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]" (output of "lspci | grep VGA") if that's any help.

---

### Post by disturbedite on 2007-03-03
if it works fine on automatic, then leave it be.  if you're getting poor performance tho, there is a command you can do that tells you the output you're looking for, but i can't remember it at the moment....someone will prolly post it and then you can try it and set beryl accordingly.

---

### Post by mcduck on 2007-03-03
With that guide, you'll be using AIGLX :)

---

### Post by rainwalker on 2007-03-03
Is that good? I mean, does AIGLX run better than XGL?

---

### Post by daniel of sarnia on 2007-03-03
> **rainwalker said:**
> Is that good? I mean, does AIGLX run better than XGL?

with my experience yes, but the ATi drivers you are using are still a bite fresh so that is likly going to be your biggest problem. But if you use the closed ati drivers it might work better but then you'd have to use xgl.

edit: if it's working fine lave it, open drivers are preferable over closed ones and AIXGL seems to work better for me....

---

### Post by mcduck on 2007-03-03
> **rainwalker said:**
> Is that good? I mean, does AIGLX run better than XGL?

It depends on your hardware. In theory AIGLX is better, but if your hardware/drivers don't support it well then XGL can be better. On my laptop's Mobility Radeon X1600 open source drivers and AIGLX are simply out of the question, but fglrx drivers & XGL perform great..

Anyway, if everything is working for you now, I don't see any reason to change it. If it's not broken, don't try to fix it ;)

---

### Post by rainwalker on 2007-03-03
I'm not really trying to fix anything, I'm more trying to speed things up. Like, I can't have windows doing too many effects (like fading out when not focused, sometimes the wobbly windows don't move smoothly, ec.).

---

### Post by mcduck on 2007-03-05
In that case you could try fglrx drivers & XGL, as Beryl is tunning really smooth with them on my desktop machine's 9600XT.

---

### Post by rainwalker on 2007-03-05
Are they buggy?

---

