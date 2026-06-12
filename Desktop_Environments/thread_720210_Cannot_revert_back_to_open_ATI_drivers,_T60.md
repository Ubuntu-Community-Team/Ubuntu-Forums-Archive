---
title: "Cannot revert back to open ATI drivers, T60"
date: 2008-03-10
forum: Desktop Environments
---

### Post by klapczuk on 2008-03-10
Hi,
I cannot revert back to open source ATI dirvers. I have Thinkpad T60 (ATI X1400) and it worked on this some time ago. Next I have installed the proprietary restricted drivers but they worked worse than open source. So I tried to reinstall open source, without success. What I tried was:
- Ubuntu 7.10
- I removed restricted drivers package
- I removed the fglrx drivers
- I modified the xorg.conf file - to use "ati" driver
- I reinstalled libgl1-mesa-glx and libgl1-mesa-dri packages
- glxinfo still outputs " Xlib: extension "GLX" missing on display ":0.0"
- I tried also to use Envy, but it doesn't help

After reboot I think the Xserver cannot load the driver and goes to failsafe session. How can I repair and debug it?

Krzysztof

---

### Post by ImAnOgre on 2008-03-10
Download and install ENVY.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Use it to remove the drivers.  It will install the open source drivers for you.

---

### Post by klapczuk on 2008-03-11
I had tried it before, I tried it once again. It doesn't help. 
Everytime the X server is restarted, it uses failsafe config. When I removed the xorg.conf file, the X server probed for several configs (including ati) and in the end started the VESA driver. How can I force it to use ati drivers??? Ati driver specification in the xorg.conf doesn't help and make it to start in failsafe mode.

---

### Post by zxscooby on 2008-03-11
did you follow these instructions?
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by klapczuk on 2008-03-11
Yes, I followed exactly. It still fails to failsafe session during X server restart. For me seems that ati driver is not loaded correctly. I can provide with any logs if it can help.

Regards,

klapczuk

---

