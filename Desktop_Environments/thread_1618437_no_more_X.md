---
title: "no more X"
date: 2010-11-10
forum: Desktop Environments
---

### Post by danielsender on 2010-11-10
Hi,

I have a Dell precision M50 which has the NVIDIA Quadro4 500 GoGL. When I upgraded from 10.04 to 10.10 the proprietary NVIDIA driver stopped working. At that time I found a simple solution which was to replace in the xorg.conf file the line in the Section "Device":

    Driver "nvidia"

by:

     Driver "nv"

giving up the accelerated features.

The other day I decided to look around for a solution and found:

[http://www.rmic.be/ubuntu-maverick-nvidia-x-problem](http://www.rmic.be/ubuntu-maverick-nvidia-x-problem)

It updated a bunch of packages but it didn't work with the NVIDIA drivers. So when I replaced again the Driver line "nvidia" with "nv", it didn't work either as before. The Xorg.1.log file is attached below in a zip file. The significant lines are:

```
[    25.341] (EE) NV: The PCI device 0x10de017c (Quadro4 500 GoGL) at 01@00:00:0 has a kernel module claiming it.
[    25.341] (EE) NV: This driver cannot operate until it has been unloaded.
[    25.341] (EE) No devices detected.
[    25.341]
Fatal server error:
[    25.341] no screens found
[    25.341]
Please consult the The X.Org Foundation support
     at http://wiki.x.org
 for help.
[    25.341] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[    25.342]
```On the other hand when I keep the Driver line to be "nvidia" I get the Xorg.1.log.old which is also in the zip attachment below shows:

```
[    25.242] (II) Loading extension DRI2
[    25.242] (II) LoadModule: "nvidia"
[    25.242] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    25.243] dlopen: /usr/lib/xorg/modules/drivers/nvidia_drv.so: undefined symbol: miEmptyData
[    25.249] (EE) Failed to load /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    25.249] (II) UnloadModule: "nvidia"
[    25.250] (EE) Failed to load module "nvidia" (loader failed, 7)
[    25.250] (EE) No drivers available.
[    25.250]
Fatal server error:
[    25.250] no screens found
[    25.250]
Please consult the The X.Org Foundation support
     at http://wiki.x.org
 for help.
[    25.250] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[    25.250]
```I don't longer care about the nvidia drivers, at least I want to get my display running. Thanks in advance.

Daniel

---

### Post by crimsonsky69 on 2010-11-10
I have similar problem. I have a on-board GPU and dedicated nvidia on my laptop. everything works fine with nvidia propriety driver disabled. But when it's enabled, it goes starit to the terminal. trying to start the x server by "startx" will say that there is no device detected.

---

### Post by madtom1999 on 2010-11-14
I've just upgraded from 10.4 to 10.10 
I've a FeForce2 MX200 that worked v well under 10.4
now I've just got console login
on startx I get to
Loading /usr/lib.xorg/extra-modules/nvidia-drv.so
dlopen: Loading /usr/lib.xorg/extra-modules/nvidia-drv.so:undefined symbol: miEmptyData

---

### Post by llelectronics on 2010-11-14
@danielsender & crimsonsky69 

*nv* is outdated. Try to use *nouveau* instead. 
If you want the nvidia drivers to work boot with the bootoption *nomodeset*
You can do so by entering the bootmenu and pressenng e at the appropiate bootentry then edit and add the bootoption in the linux line. To boot then use CTRL+X. 

@madtom1999 

I don't think your old card is supported by Nvidia anymore. Try using the nouveau driver instead.

---

### Post by danielsender on 2010-11-15
I just found that there is a new driver from nvidia 96.43.19 that was released on 11/02/10 and it works well with my machine. The only problem is that it does not appear in the "Additional Drivers" field of "Administration" which precludes setting the "Appearance Preferences"->"Visual Effects" to anything but "None".

---

### Post by slaked on 2010-11-15
me too
i was having problems with the nvidia driver, it started when i updated the driver and it would not work anymore.

---

### Post by ryankask on 2011-01-01
Any updates on this issue?

I have:

```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 330M] (rev a2)

```

Same issue....no glx. See [my post on the issue]("http://ubuntuforums.org/showthread.php?p=10304014") for more details.

Ryan

Thanks,
Ryan

---

