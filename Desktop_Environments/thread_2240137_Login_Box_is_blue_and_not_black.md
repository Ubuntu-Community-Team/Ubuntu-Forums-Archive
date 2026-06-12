---
title: "Login Box is blue and not black"
date: 2014-08-18
forum: Desktop Environments
---

### Post by makkekkazzo on 2014-08-18
Hi Guys, 

after last upgrade some colours and option have changed, but luckily I found, via these forums, that was a xorg-server problem, or something so, and all get back to normality. The point is that the box for the login, the one where password is written, unfortunately has still a blue underground and not black as usual. Does somebody know how to fix it? I know that is not a big matter but I fear that there are other changes that I don't have already seen.

Thanks a lot

Regards

---

### Post by Frogs Hair on 2014-08-18
Please post the Ubuntu version . The box in my standard Ubuntu 14.04 installation is semitransparent.

---

### Post by makkekkazzo on 2014-08-20
Sorry,```
makkekkazzo@fra:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise


```

---

### Post by Frogs Hair on 2014-08-20
Login should look like the picture below with the default background. If you have installed any other desktop environments such as Xubuntu (example) this will change the login background and greeter box appearance . Have you tried other desktops?

---

### Post by makkekkazzo on 2014-08-21
No I haven't tried any other desktop. Some time ago in the upgrade windows appeared a "new Hardware support" option. After some tries I succeeded to install it but after some colours and some little things changed (for example the sidebar was black and not violet), I managed to solve it via a walkthrough (was something related to xorg-server). Now the only thing that has remained is that the little box for the password is not like the one in your photo, all the rest is the same underground color and logos. My box now doesn't have rounded corner and the color is blue. Is there the possibility to take a screenshot of my login window?

Thanks

---

### Post by Frogs Hair on 2014-08-21
Reinstalling the package, unity-greeter might help ,but if the configuration file is somehow corrupt it won't change anything. The screen capture tool won't work prior to login.

---

