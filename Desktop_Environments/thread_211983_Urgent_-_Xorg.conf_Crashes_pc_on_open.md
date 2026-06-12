---
title: "Urgent - Xorg.conf Crashes pc on open"
date: 2006-07-09
forum: Desktop Environments
---

### Post by CheeseAndToast on 2006-07-09
Helllpppppppp!![-o< 

I've installed compiz, using [this thread]("http://ubuntuforums.org/showthread.php?t=145068")

on step 2 i have to config xorg.conf.  I'v made a back up when i enter
sudo gedit /etc/X11/xorg.conf, the PC freezes! Nothing works!!:shock: 

please help!!

Thanks

---

### Post by raldz on 2006-07-09
try to boot in recovery mode, then execute this:

```
dpkg-reconfigure xserver-xorg
```

choose the default options to login to the desktop manager, then try to figure out later what went wrong..

---

### Post by CheeseAndToast on 2006-07-09
Thanks for the reply - keeps crashing randomly!!

I've rebooted it recovery mode and executed the above code.
I'll try to continue, i'll let you what happens.
I didn't actually configure anything, all I did was rename it. I think its to do with compiz?

---

### Post by CheeseAndToast on 2006-07-09
for those of who you who where really worried about my system, i'm pleased to say the issue has been resolved by a rreinstall!

cheers.

---

