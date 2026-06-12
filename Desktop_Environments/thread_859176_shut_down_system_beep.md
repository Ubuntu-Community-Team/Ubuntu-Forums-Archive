---
title: "shut down system beep?"
date: 2008-07-14
forum: Desktop Environments
---

### Post by stargirl51 on 2008-07-14
Does anyone know how to turn off the system/console beep that happens when you shut down in xfce?

It's quite embarassing when you're in the middle of a study hall and there's a loud system beep...

Thanks in advance!

---

### Post by o.besner on 2008-07-14
Yes, there is a simple way to mute it forever. Since the sound is coming from your pc integrated speaker (the one that only do beeps, not your laptop ones), you can blacklist the module. If you want to keep it though, you can remove it temporarily.

If you want to remove it temporarily.

in the console, type:

```
sudo modprobe -r pcspkr
```

If you want to remove it permanently, you gotta tell modprobe to never load this module.

In the console, type this : (replace nano with your favorite text editor)

```
sudo nano /etc/modprobe.d/blacklist
```

scroll down to the bottom of the document, and add this :

# this is how you mute annoying beeps in console and shutdown
blacklist pcspkr

The pounded part (#) is optional, but if you ever want to bring back the beep it'll help you know what do you.

---

### Post by stargirl51 on 2008-07-14
Thank you so much!!

---

### Post by DavidVanCan on 2008-11-13
> **o.besner said:**
> Yes, there is a simple way to mute it forever...

Thanks o.besner, works like a charm!

---

