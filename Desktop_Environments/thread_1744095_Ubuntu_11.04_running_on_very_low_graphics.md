---
title: "Ubuntu 11.04 running on very low graphics"
date: 2011-04-30
forum: Desktop Environments
---

### Post by coolvishesh on 2011-04-30
Yesterday i upgraded my ubuntu to version 11.04.. but found that its running on very low graphics.. My additional driver for nvidia are also activated but it seems they are not working...
i cannot even see the new 11.04 theme and unity is also not working.. 
Desktop looks like as if my using 10.04 version of ubuntu..Ubuntu is not working with its full graphics on.

My system(Laptop) configuration is:
Model: HP Dv6000 series
RAM:4GB
Graphics:nvidia 8400 GM
Processor: 2ghz
HDD:320GB
Additional OS: Windows 7 installed alongside ubuntu

Please help me get the real graphics for Ubuntu 11.04..
Thanks much in advance.

---

### Post by Krytarik on 2011-04-30
Try reinstalling the proprietary Nvidia driver, check its version in "Additional Drivers", for "current" run:
```
sudo apt-get install --reinstall nvidia-current
```
Otherwise "nvidia-XXX".

Greetings.

---

