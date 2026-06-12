---
title: "Install plain kde over ubuntu alternate cd"
date: 2006-11-11
forum: Desktop Environments
---

### Post by reldruH on 2006-11-11
I'd like to see what default kde is like, without all of the modifications Kubuntu adds (but I want the ubuntu base for things like upstart). I have an alternate CD so I can install the base system (sans any desktop environment) but I haven't been able to find any tutorials on how to install basic kde on top of that (or the ones I have found haven't worked). Any ideas on how to get plain kde on top of ubuntu?

---

### Post by Velotix on 2006-11-11
The vanilla version of KDE is in the Ubuntu repositories under "kde-core", or something very similar. That should do the trick (haven't used it myself). Installing it from aptitude would be your best bet, methinks.

---

### Post by reldruH on 2006-11-11
> **Velotix said:**
> The vanilla version of KDE is in the Ubuntu repositories under "kde-core", or something very similar. That should do the trick (haven't used it myself). Installing it from aptitude would be your best bet, methinks.

That was actually one of the methods that I tried. I installed just the base and then did ```
sudo aptitude update && sudo aptitude install kde-core
sudo /etc/init.d/kdm start
``` I got the message that kdm was already running, but still only had a cli. When I tried to start x I got an error message about fonts not being found. I know that I need more than just the basic kde-core but I don't know what else and google hasn't really helped me find anything.

---

### Post by Velotix on 2006-11-11
(Checking for anything that might be useful in Synaptic, will edit this post as I come across them.)

> When I tried to start x I got an error message about fonts not being found.

```
sudo aptitude update && sudo aptitude install defoma
```

The font manager for Debian (and thus Ubuntu).

> I got the message that kdm was already running, but still only had a cli.

```
sudo aptitude update && sudo aptitude install kdebase kdelibs kdesktop
```

---

### Post by reldruH on 2006-11-12
> **Velotix said:**
> (Checking for anything that might be useful in Synaptic, will edit this post as I come across them.)

Thank you very much for your help. I'm going to test all this out tomorrow morning and see if that doesn't fix it. I'll update here and let you know if it works. Again, thanks:)

---

