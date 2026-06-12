---
title: "Adding an additional GPU | 14.04.4"
date: 2016-06-22
forum: Desktop Environments
---

### Post by jimmy53 on 2016-06-22
Hi I have a fresh install of ubuntu 14.04.4 and I am having problems with aticonfig recognising the second GPU.

It is usually a matter of..


aticonfig --initial -f --adapter=all

reboot

Win!

Although after I reboot the xorg.conf gets overwritten and I cannot set clocks, fan etc with aticonfig/od6config.

I would rather have manual control over the fans and setting the core clocks is impossible.


I've switch GPU's around, tried different slots to no avail and even disabled gpu-manager.

I have tried the fglrx from APT and also latest crimson drivers from AMD to no avail.

I have linked the output of various commands to see it will help solve my problem.

[http://pastebin.com/BDH3Frse](http://pastebin.com/BDH3Frse)

Thanks

---

### Post by jimmy53 on 2016-06-22
Eureka!, Problem solved. 
Disable gpumanager.

```
sudo vi /etc/default/grub
```

Add "nogpumanager" in the following line
e.g. if you have this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

it should look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nogpumanager"
```

Esc :wq  to write changes and quit.

```
sudo update-grub
```

Reboot

Make sure that the following command returns true:
```
grep nogpumanager /proc/cmdline && echo true || echo false

```
If it returns true, regenerate the xorg.conf
```
sudo aticonfig --adapter=all --initial
```

=======================

export DISPLAY=:0

```
sudo aticonfig --adapter=all --odgc

Adapter 0 - Supported device 67B1
                            Core (MHz)    Memory (MHz)
           Current Clocks :    300           150
             Current Peak :    947           1250
  Configurable Peak Range : [300-1500]     [150-2000]
                 GPU load :    0%

Adapter 1 - Supported device 67B1
                            Core (MHz)    Memory (MHz)
           Current Clocks :    300           150
             Current Peak :    947           1250
  Configurable Peak Range : [300-1500]     [150-2000]
                 GPU load :    0%
```

Thank goodness for that!

---

