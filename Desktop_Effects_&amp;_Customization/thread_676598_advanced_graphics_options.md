---
title: "advanced graphics options"
date: 2008-01-23
forum: Desktop Effects &amp; Customization
---

### Post by SiCkTiB on 2008-01-23
is there any way to enable it. i had bought my notebook with ubuntu gutsy already installed on it and noticed they did not put the advanced graphics option on here. do i have to reinstall ubuntu to get access to this option?

---

### Post by chewearn on 2008-01-24
-
What is your PC specs, specifically the graphics?

-

---

### Post by SiCkTiB on 2008-01-24
its a Dell notebook Inpirion 1420

2.6GHz dual core 2 Intel
2GB ram
128 nVidia Graphics Card ( I know kinda sucky but only option they had for graphics)

that should tell about the graphics right there
now that im looking at it maybe the 128MB graphics card might be the problem. but i put it on the most visual effects and it works fine with no lag.

---

### Post by chewearn on 2008-01-24
First of all, is the nvidia restricted driver enabled?  Find out here:
Top Panel Menu > System > Administration > Restricted Driver Manager

If not enabled, try that first.  Then reboot, check if direct rendering is enabled.  Run this command in terminal:
```
glxinfo | grep rendering
```

---

