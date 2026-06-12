---
title: "Steam on Ubuntu 12.04 LTS does not work, i need help."
date: 2013-06-05
forum: Gaming &amp; Leisure
---

### Post by Andrukles on 2013-06-05
Hi there. I try to install Steam on my Ubuntu computer, i use Ubuntu 12.04 LTS. My computer is MSI-CX623-051NE with Nvidia 310M Cuda.
when i run steam through terminal i receive this message:

Running Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1370457613_client)
Xlib:  extension "GLX" missing on display ":0".
Installing breakpad exception handler for appid(steam)/version(1370457613_client)
Installing breakpad exception handler for appid(steam)/version(1370457613_client)
unlinked 0 orphaned pipes
removing stale semaphore last operated on by process 6868 with name 0eBlobRegistryMutex_C7AFFFECF67AAE6C8B771AE09D5FE700
removing stale semaphore last operated on by process 6868 with name 0eBlobRegistrySignal_C7AFFFECF67AAE6C8B771AE09D5FE700
removing stale semaphore last operated on by process 6868 with name 0emSteamEngineInstance
removing stale semaphore last operated on by process 6868 with name 0eSteamEngineLock
Xlib:  extension "GLX" missing on display ":0".

---

### Post by efflandt on 2013-06-05
It looks like you are missing GLX. Are you running the recommended experimental nvidia drivers installed using Additional Drivers, or the default nouveau video drivers?

This command should return something like this:```
efflandt@xps8100-1204:~$ dpkg-query -l nvidia*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
un  nvidia-180-modaliases       <none>                      (no description available)
un  nvidia-185-modaliases       <none>                      (no description available)
ii  nvidia-common               1:0.2.44.2                  Find obsolete NVIDIA drivers
un  nvidia-current-modaliases   <none>                      (no description available)
rc  nvidia-experimental-304     304.48-0ubuntu0.1           Experimental NVIDIA binary Xorg driver, kernel module and VDPAU librar
ii  nvidia-experimental-310     310.14-0ubuntu0.3           Experimental NVIDIA binary Xorg driver, kernel module and VDPAU librar
ii  nvidia-settings-experimenta 304.48-0ubuntu0.1           Tool of configuring the NVIDIA graphics driver
in  nvidia-settings-experimenta <none>                      (no description available)
```

---

### Post by Andrukles on 2013-06-06
I use the experimental driver from Ubuntu store called "Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library".

---

### Post by Andrukles on 2013-06-06
helmer@helmer-MS-168A:~$ dpkg-query -l nvidia*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  nvidia-180-mod <none>         (no description available)
un  nvidia-185-mod <none>         (no description available)
ii  nvidia-common  1:0.2.44.2     Find obsolete NVIDIA drivers
un  nvidia-current <none>         (no description available)
ii  nvidia-current 304.88-0ubuntu NVIDIA binary Xorg driver, kernel module and
ii  nvidia-experim 310.14-0ubuntu Experimental NVIDIA binary Xorg driver, kern
ii  nvidia-setting 310.14-0ubuntu Tool for configuring the NVIDIA graphics dri
ii  nvidia-setting 304.88-0ubuntu Tool of configuring the NVIDIA graphics driv

---

### Post by Andrukles on 2013-06-06
My computer use Nvidia 310M cuda.

---

### Post by CatKiller on 2013-06-07
Is that an Optimus thing?

---

### Post by Perfect Storm on 2013-06-07
A search on google says it's an optimus card, so you can't use the regular driver. You need to get the Bumblebee driver for that.


EDIT: forget what I said, there's a guide on CUDA cards here: [http://askubuntu.com/questions/131506/how-can-i-get-nvidia-cuda-or-opencl-working-on-a-laptop-with-nvidia-discrete-car](http://askubuntu.com/questions/131506/how-can-i-get-nvidia-cuda-or-opencl-working-on-a-laptop-with-nvidia-discrete-car)

---

