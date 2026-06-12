---
title: "Monitor Disconnecting For A While on Startup..."
date: 2016-03-16
forum: Desktop Environments
---

### Post by Ravi_Raj on 2016-03-16
Hello there,

Recently installed Ubuntu 14.04. Using HP-w17e monitor and AMD Radeon Graphics card. Everything works fine after installation, but I had seen that while switching on the system or restarting, the monitor automatically disconnects itself (red light blinking) for few seconds and then the login screen comes.

Is there a option from which I can stop this disconnection.

---

### Post by grahammechanical on 2016-03-16
I do not think so. What you are seeing comes about because of the complicated way that a Linux distribution loads and the fact that modern digital displays are designed to shut down if the video signal is no longer present.

As far as I can work things out we start with the motherboard having a default video setting. That is what we get when the Linux boot menu appears. Then Linux starts to load and at some point Linux makes an inquiry of the monitor as to the optimum screen settings. Then a video driver is loaded. meanwhile Linux continues loading and then has to load a desktop user interface. During this process the signal from the video adapter drops for a few seconds.

This is life at the moment with Linux.

Regards

---

### Post by Ravi_Raj on 2016-03-16
Hi GrahamMechanical,

You are absolutely right. But, will you please tell me a solution.

Thanks in advance.

---

