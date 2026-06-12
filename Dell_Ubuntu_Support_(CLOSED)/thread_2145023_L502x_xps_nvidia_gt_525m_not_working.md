---
title: "L502x xps nvidia gt 525m not working"
date: 2013-05-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by knapie on 2013-05-14
Hi all, I'm at my wits' end trying to get the NVIDIA card going in my Dell XPS L502X.

I've read many threads and tried many things, but I'm stuck.

I know the card is there:

```

:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 525M] (rev a1)

```

These are the drivers I have installed:
```

:~$ dpkg -l | grep nvidia
ii  bumblebee-nvidia                              3.2.1-1~raringppa2                        amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
rc  nvidia-304                                    304.88-0ubuntu1                           amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-304-updates                            304.88-0ubuntu2                           amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-310                                    310.44-0ubuntu2                           amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-310-updates                            310.44-0ubuntu2                           amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                                 1:0.2.76                                  amd64        transitional package for ubuntu-drivers-common
ii  nvidia-current-updates                        304.88-0ubuntu2                           amd64        Transitional package for nvidia-current-updates
rc  nvidia-settings                               304.88-0ubuntu0.2                         amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-settings-304                           304.88-0ubuntu1                           amd64        Tool for configuring the NVIDIA graphics driver

```

When I try and run nvidia-settings, I get an error message:
> 
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server/


When I try and run 'nvidia-xconfig', I get:
> 
sudo: nvidia-xconfig: command not found


Running anything with bumblebee, I get the following:
```
~$ optirun glxspheres 
[ 3865.244059] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) No devices detected.


[ 3865.244161] [ERROR]Aborting because fallback start is disabled.

```

Any pointers would be greatly appreciated.

I'm trying to switch completely to Linux, but I need to be able to run some engineering software with proper 3D hardware, which the NVIDIA card should be more than capable of doing.  Failing that, it's a bit of a show-stopper.

Thank you for your input.

---

