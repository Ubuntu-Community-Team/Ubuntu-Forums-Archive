---
title: "Color calibration"
date: 2010-04-14
forum: Desktop Environments
---

### Post by rozbarwinek on 2010-04-14
Hi

Is there any monitor calibration application for kubuntu?
openSUSE has something like this --> 

[[IMG]http://img227.imageshack.us/img227/6995/zrzutekranu26.th.png[/IMG]](http://img227.imageshack.us/i/zrzutekranu26.png/)

Can I have something like this on kubuntu?
I have to calibrate my display and I don't want to use ATI control panel because I am using open source drivers.

---

### Post by Untitled_No4 on 2010-04-14
You have to install kgamma. Either from KPackageKit or in Konsole running
```
sudo aptitude install kgamma
```

Then open System Settings (you have to close it first if it's already open) and in Display you will have the gamma calibration module.

---

### Post by rozbarwinek on 2010-04-14
> **Untitled_No4 said:**
> You have to install kgamma. Either from KPackageKit or in Konsole running
```
sudo aptitude install kgamma
```

Then open System Settings (you have to close it first if it's already open) and in Display you will have the gamma calibration module.

Thanks :D

---

