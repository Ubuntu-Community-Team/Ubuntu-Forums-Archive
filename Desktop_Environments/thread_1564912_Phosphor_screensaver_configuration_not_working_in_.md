---
title: "Phosphor screensaver configuration not working in ubuntu 10.4"
date: 2010-08-31
forum: Desktop Environments
---

### Post by gwiener on 2010-08-31
I've upgraded recently to ubuntu 10.4. I had the phosphor screensaver configured to run a custom command by editing the phosphor.desktop file. After the upgrade, no matter what I do, the gnome screensaver ignores the configuration. Instead, it just shows some logs from the Ubuntu mailing list or something like that. I want the command that I configured back!

Thanks.

---

### Post by roobarb! on 2010-11-14
Easiest way I've found is to replace gnome-screensaver with xscreensaver. Just remove gnome-screensaver using Synaptic and then install xscreensaver. Then add a Startup Application that has the command:

```
xscreensaver -nosplash
```

You'll then find a cornucopia of configuration options at your disposal under the Screensaver window. Much better.

---

