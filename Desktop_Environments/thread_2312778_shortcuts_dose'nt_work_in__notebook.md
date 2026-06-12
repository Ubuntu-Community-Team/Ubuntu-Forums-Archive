---
title: "shortcuts dose'nt work in  notebook"
date: 2016-02-07
forum: Desktop Environments
---

### Post by mehdi10 on 2016-02-07
Hi

I bought hp probook 450 g3 . 
I installed ubuntu 15.10 . shortcuts does'nt work in it. fn+f5 for change brightness.

```
01:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265] [1002:6900] (rev 83)
```

---

### Post by Vladlenin5000 on 2016-02-08
What driver are you using? You probably need AMD proprietary drivers (fglrx) for better performance, power management and yes, brightness keys and stuff.

---

### Post by mehdi10 on 2016-02-08
> **Vladlenin5000 said:**
> What driver are you using? You probably need AMD proprietary drivers (fglrx) for better performance, power management and yes, brightness keys and stuff.
I am  using *xserver-xorg-video* .
When my notebook go to hibernate . never it turn on .

---

### Post by Vladlenin5000 on 2016-02-08
So, already answered. Nothing else to add unless you need help testing the proper AMD drivers.

---

### Post by amir-shehzad on 2016-12-27
[mehdi10]("https://ubuntuforums.org/member.php?u=1993199")[COLOR=#000000] according to ubuntu website, HP Probook 450 G3 is currently not supported. Since i have same model, i also ran into same problems. This model uses hybrid hardware (intel+amd radeon) for display, ubuntu driver of which is i think currently being developed. So solution is to go to bios and change display from Hybrid to UMA. if this does't solve problem, you need to reinstall ubuntu with this changed settings.
webiste:
 [https://certification.ubuntu.com/certification/make/HP/?query=hp+probook+450&category=Desktop&category=Laptop&category=Server&release=&level=Any](https://certification.ubuntu.com/certification/make/HP/?query=hp+probook+450&category=Desktop&category=Laptop&category=Server&release=&level=Any)[/COLOR]

---

