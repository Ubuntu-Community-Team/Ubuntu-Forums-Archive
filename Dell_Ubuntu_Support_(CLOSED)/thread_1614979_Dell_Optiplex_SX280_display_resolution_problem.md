---
title: "Dell Optiplex SX280 display resolution problem"
date: 2010-11-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by HannuMR on 2010-11-06
Display LG Flatron L1915S needs resolution 1280 x 1024, but biggest by Ubuntu 10.04.1 is 1024 x 768. 
View is not good.
I simple like that Dell Optiplex.
So, is it necessary to change display, computer, my self, or is there any solution for better view?


:confused:

---

### Post by linux-hack on 2010-11-06
What graphic card do you have ? Did you install the proprietary drivers ? If you go to System=Administration=Install Drivers or something like that .. you can install the drivers. 

If you have them try reconfiguring them like this :

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by HannuMR on 2010-11-06
> **linux-hack said:**
> What graphic card do you have ? Did you install the proprietary drivers ? If you go to System=Administration=Install Drivers or something like that .. you can install the drivers. 

If you have them try reconfiguring them like this :

```
sudo dpkg-reconfigure xserver-xorg
```

There is not drivers in Ubuntu for graphic card, because it is integrated.

[http://support.euro.dell.com/support/edocs/systems/opsx280/en/ug/specs.htm](http://support.euro.dell.com/support/edocs/systems/opsx280/en/ug/specs.htm)

At the same time, Dell gives many different resolutions for displays on Optiplex SX280.
So is the reason in Ubuntu because I can not use drivers for Windows?

[http://www.freeimagehosting.net/uploads/b2340575e5.png](http://www.freeimagehosting.net/uploads/b2340575e5.png)

---

