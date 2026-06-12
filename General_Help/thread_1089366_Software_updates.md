---
title: "Software updates"
date: 2009-03-07
forum: General Help
---

### Post by fa355115 on 2009-03-07
Hi there !

After a first installayion of ubuntu, I have a problem with my wifi routeur not recognized (invisible).

Instead of following some procedure I found on this forum without understanding what I was doing or even if it was applicable to me

[http://ubuntuforums.org/showthread.php?t=493095&highlight=4965.]("http://ubuntuforums.org/showthread.php?t=493095&highlight=4965.")

, I choosed first to update my system with the latest updates **264 !!**

Then the system, rebooted.

Is there a way I can check which updates were installed (for exa,ple if I'd like to see if something was installed for my wifi ?)

Many thanks !

---

### Post by martrn on 2009-03-07
> **fa355115 said:**
>  ..... Is there a way I can check which updates were installed (for exa,ple if I'd like to see if something was installed for my wifi .... 

Try :-

```
ls /var/cache/apt/archives -altr
```

To see whats in your apt-cache  (sorted by date order.

---

