---
title: "Cannot start Swiftfox"
date: 2006-09-05
forum: Desktop Environments
---

### Post by Rhapsody on 2006-09-05
After reinstalling Kubuntu, I have found myself unable to start up [Swiftfox](http://www.getswiftfox.com/). Attempting to start the application through Konqueror does nothing, and trying to start it through Konsole produces the following:

```
swiftfox/swiftfox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory
```

libmozjs.so is present in the main Swiftfox folder and a fresh install produces the same problems. What's going on?

---

### Post by taurus on 2006-09-05
You need to include whatever the directory that contains that library in your /etc/ld.so.conf so swiftfox can find it...

---

### Post by Rhapsody on 2006-09-05
> **taurus said:**
> You need to include whatever the directory that contains that library in your /etc/ld.so.conf so swiftfox can find it...
I don't see that file anywhere.

---

### Post by Rhapsody on 2006-09-06
I still haven't figured out what I'm supposed to be doing. No offense to Konqeuror and the KDE Team, but Swiftfox is really the best browser I've ever used.

---

### Post by Stirling on 2006-09-06
How are you launching Swiftfox?  It should be started by running *swiftfox* and not *swiftfox-bin*.

---

