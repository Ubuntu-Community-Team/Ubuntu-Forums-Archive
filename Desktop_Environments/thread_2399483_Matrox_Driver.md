---
title: "Matrox Driver"
date: 2018-08-25
forum: Desktop Environments
---

### Post by danielsender on 2018-08-25
I have a vintage Dell Dimension 1100 (32b). This machine has an integrated graphic system. I did an upgrade from 16.04 to 18.04. The upgrade went well, but when I rebooted the system, it got stuck with the red screen. I posted the issue on "Installation and Upgrades", and after getting some help I realized that the problem was the graphic system. I had an old PCI Matrox card MGA 1064SG, which I installed. That appeared to solve the black screen problem but the resolution I'm getting cannot be higher than 1024x768. My monitor is 1280x1024. I assume that this is because I should have the proper driver, which I understand is the xserver-xorg-video-mga, but I cannot find it in synaptic. I would appreciate it if someone can give me some pointers about this.

Thanks.

---

### Post by SeijiSensei on 2018-08-26
I have 

/lib/modules/4.15.0-33-generic/kernel/drivers/gpu/drm/mgag200/mgag200.ko

on my system.  That should be the Matrox driver.  I don't think it's much supported any more.

What if you run

```
sudo modprobe mgag200
```

---

### Post by danielsender on 2018-08-26
It is there:

/lib/modules/4.15.0-33-generic/kernel/drivers/gpu/drm/mgag200/mgag200.ko

However when I do 'sudo modprobe mgag200', I get:

modprobe: ERROR: could not insert 'mgag200': Invalid argument

what should I do?

Thanks

---

### Post by danielsender on 2018-08-27
I think that your statement: [B]If you ask for help, do not abandon your request. Please have the courtesy to check for responses and thank the people who helped you.

[/B]should also applied to those who are responding.

But thanks anyway.

---

### Post by SeijiSensei on 2018-08-29
I've told you everything I know on this subject, I'm afraid.

---

### Post by danielsender on 2018-08-29
That's fine, I appreciate your input anyway.

---

