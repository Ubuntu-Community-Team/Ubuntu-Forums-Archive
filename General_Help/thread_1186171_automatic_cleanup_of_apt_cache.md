---
title: "automatic cleanup of apt cache"
date: 2009-06-13
forum: General Help
---

### Post by dondos on 2009-06-13
Hello everybody.

My system (Jaunty) keeps automatically deleting the locally cached .deb packages from my /var/cache/apt/archives directory. All .deb files that are older than one month are gone.

The strange thing is that I modified my /etc/apt/apt.conf.d/20archive right after I installed Jaunty. My disk has a lot of free space, so my choice was not to erase the local apt cache.

My 20archive reads as follows:

```
APT::Archives::MaxAge "0";
APT::Archives::MinAge "0";
APT::Archives::MaxSize "0";
```

So why is this happening? Should I do something more to stop this automatic cleanup from happening?

Thank you in advance.

---

### Post by Legace on 2009-06-13
Open Synaptic -> Settings -> Preferences -> Files tab, and make sure the settings are set the way you want.

---

### Post by dondos on 2009-06-13
This must be it. I never noticed there was an option to "Leave all downloaded packages in the cache". The default option was to "Delete packages that are no longer available".

I will test if this works, and I will soon mark this thread as closed. Thank you very much!

---

### Post by dondos on 2009-06-18
No, it still doesn't work... I did change the option I was told but the problem persists. Yesterday (17 June), all the packages that were updated on the 16th of May were gone.

Is there something else I could do to remedy this situation?



**UPDATE:** After a lot of testing, I strongly believe that /etc/apt/apt.conf.d/20archive is totally ignored by the system. I tried many different (zero and non-zero) values, but the result is always the same.

---

