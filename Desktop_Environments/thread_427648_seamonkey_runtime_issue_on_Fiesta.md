---
title: "seamonkey runtime issue on Fiesta"
date: 2007-04-29
forum: Desktop Environments
---

### Post by brian.smith on 2007-04-29
I installed seamonkey (new name for the all-in-one mozilla suite) from mozilla.org, and now when I try to run it I get the following:

./seamonkey-bin: error while loading shared libraries: libxpcom.so: cannot open shared object file: No such file or directory

Any clues? Interestingly, I had gotten the same error during installation time of seamonkey, but when I immediately tried again to install, it installed fine. 

libxpcom.so seems to be used by firefox as well (which runs fine on the system).

As an aside - anyone know why mozilla suite was dropped from 7.04? I specifically used mozilla composer extensively, and having mozilla around as an alternative browser was always good.

Thanks

---

### Post by paparucino on 2007-04-30
> **brian.smith said:**
> 
libxpcom.so seems to be used by firefox as well (which runs fine on the system).


Yes it is.
```

/root/thunderbird/libxpcom.so
/usr/lib/firefox/libxpcom.so
/usr/lib/mozilla-thunderbird/libxpcom.so
/usr/lib/swiftfox/libxpcom.so
/usr/local/share/firefox/libxpcom.so

```
I think you should check if the library is installed in /usr/lib/seamonkey (or something like)
otherwise you could sym link it to the firefox one









UAResolved

---

