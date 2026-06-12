---
title: "Natty 11.04 | Bluetooth Not Detected"
date: 2011-05-01
forum: Desktop Environments
---

### Post by arnelcolar on 2011-05-01
My laptop (eMachines D730) has bluetooth but Natty does not detect it. Is there any way to enable bluetooth in Natty? Should I download drivers for it? 

If so, could anyone suggest how to install my bluetooth's driver? This is the model name of my laptop's bluetooth: **FOXCONN BCM92056**

Any help would be much appreciated.

---

### Post by arnelcolar on 2011-05-12
Nice, I recieved **A LOT** of help...

The only problem is I was not able to see it.



Can I post this problem in forums?

Where forum members just stare at my post doing absolutely **NOTHING**

Is this really a forum where you help people or is this where we stare at problems and wait for it to be solved?

---

### Post by Oskenso on 2011-05-16
A tiny google search would have pointed you here:

[https://bugs.launchpad.net/system76/+bug/762964](https://bugs.launchpad.net/system76/+bug/762964)
and after reading through it you'll find the work around

```
sudo killall bluetoothd
sudo bluetoothd
```

---

