---
title: "indicator-sound reporting &quot;no watchers&quot;"
date: 2012-06-07
forum: Desktop Environments
---

### Post by Copperblade on 2012-06-07
I have the latest Xubuntu installed on my desktop and a laptop.  Both were upgraded from the previous version.  For some reason on my desktop I can't run /usr/lib/indicator-sound/indicator-sound-service.  It fails with this error:

```
libindicator-WARNING **: No watchers, service timing out.

```

It comes up automatically on my laptop, and is a superior choice to the "mixer" applet so I'd like to use it.  For the life of me, I cannot figure out the difference between the two systems or why it simply won't run on the desktop.

Is there some trick to getting it to load in the notification area?

---

### Post by LewisTM on 2012-06-07
Make sure indicator-sound-gtk2 is installed and that you have the Indicator plugin in one of your panels. This one (usually) also shows network connectivity and mail messages.

Cheers!

---

### Post by Copperblade on 2012-06-07
Thanks.  I was missing the -gtk2 package.  After that it worked on reboot.

---

