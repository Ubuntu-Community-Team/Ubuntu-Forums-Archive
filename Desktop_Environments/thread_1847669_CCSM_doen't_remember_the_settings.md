---
title: "CCSM doen't remember the settings"
date: 2011-09-21
forum: Desktop Environments
---

### Post by nlkasyap09 on 2011-09-21
Hi,

I'm new to ubuntu. I installed 11.04 recently and was trying to set up compiz cube instead of unity. In the classic mode I tried to configure CCSM, but the settings vaninshed almost instantly. Like I configured Desktop section and when i configured Effects section all the previous settings under desktop section were gone. This is just one to say. I've not been able to set up the cube. 

I set up compiz cube before but settings were lost on reboot coz i installed it in the same partition as windows is in. So then i re-installed it in another drive but settings were lost even before i can close CCSM. Please help me

---

### Post by Frogs Hair on 2011-09-21
A proprietary is required to run Compiz . A driver if available can be found in Additional Drivers .

If the driver is installed , below is a command to reset Compiz.```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
sudo reboot

```

---

