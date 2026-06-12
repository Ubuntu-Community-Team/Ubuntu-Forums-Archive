---
title: "Gnome classic gone"
date: 2014-08-23
forum: Desktop Environments
---

### Post by Svento on 2014-08-23
I logged in into Unity for some reason, and after that, Fallback won't work... Unity appears without the Global Menu when I choose Gnome Classic.

Is there a way to fix this?

---

### Post by Frogs Hair on 2014-08-23
I see from other posts you may be using 12.04 and if you are using the no effects session you could try the following .```
 metacity --replace 
```

---

### Post by Svento on 2014-08-24
I was using it with Compiz and effects. There's appearantly something very wrong with my installation, and I wouldn't be surprised if there's a hardware problem. Different unrelated issues even after a fresh install...

---

### Post by kansasnoob on 2014-08-24
> **Svento said:**
> I was using it with Compiz and effects. There's appearantly something very wrong with my installation, and I wouldn't be surprised if there's a hardware problem. Different unrelated issues even after a fresh install...

Fresh install of what version?

---

### Post by Svento on 2014-08-24
12.04. Tried to upgrade 14.04 but then the system wouldn't start at all. At first when I reinstalled 12.04, that wouldn't work either, but then by mistake I installed with a fresh Home partition instead of saving the old one and it worked. Worked more or less...

---

### Post by kansasnoob on 2014-08-24
> **Svento said:**
> 12.04. Tried to upgrade 14.04 but then the system wouldn't start at all. At first when I reinstalled 12.04, that wouldn't work either, but then by mistake I installed with a fresh Home partition instead of saving the old one and it worked. Worked more or less...

Well that tells me that you may have some borked hidden dots in your original Home. In 12.04 that was fairly easy to deal with:

[http://ubuntuforums.org/showthread.php?t=1966370&page=4&p=11968600#post11968600](http://ubuntuforums.org/showthread.php?t=1966370&page=4&p=11968600#post11968600)

Trusty (14.04) is not as easy to deal with, I still don't have it totally figured out :(

Should you decide to stick with Precise you should also know about [LTS HWE]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") and particularly [HWE EOL]("https://wiki.ubuntu.com/1204_HWE_EOL"). Well, for that matter Trusty will be effected also when 14.04.2 is released ................ just stuff to be aware of ;)

---

