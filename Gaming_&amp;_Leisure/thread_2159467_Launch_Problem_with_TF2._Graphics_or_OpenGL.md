---
title: "Launch Problem with TF2. Graphics or OpenGL?"
date: 2013-07-03
forum: Gaming &amp; Leisure
---

### Post by Hydera5 on 2013-07-03
Hello everybody, I have downloaded steam for linux as well as tf2, the only problem is when I run the game it gives me the error: Could not find OpenGL entry point 'glColorMaskInedexedEXT'!  Either you Graphics card is unsupported, or your OpenGL driver needs to be updated. 

So i ran: lshw -C video and got this:

 *-display               
       description: VGA compatible controller
       product: C67 [GeForce 7150M / nForce 630M]
       vendor: NVIDIA Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f5000000-f5ffffff memory:d0000000-dfffffff memory:f4000000-f4ffffff memory:80000000-8001ffff

Im very new to Ubuntu so I was wondering if someone could straight up if my graphics card is unsupported.
Or if its my opengl driver out of date, how i would go about updating it to fix this issue.

Thanks!

---

### Post by davetv on 2013-07-03
[http://steamcommunity.com/app/221410/discussions/0/882966056532198187/#p8](http://steamcommunity.com/app/221410/discussions/0/882966056532198187/#p8)

---

### Post by Hydera5 on 2013-07-03
> **davetv said:**
> [http://steamcommunity.com/app/221410/discussions/0/882966056532198187/#p8](http://steamcommunity.com/app/221410/discussions/0/882966056532198187/#p8)

Ok i went through and tried the first step.  But the terminal returned this:  

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libc6-dev-i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

---

### Post by efflandt on 2013-07-03
Are you running 32-bit or 64-bit Ubuntu? Steam was 32-bit. Not sure if anything in it is 64-bit yet, but it runs fine in 64-bit 12.04 with 32-bit libs (**ia32-libs** package). The **libc6-dev-i386** in that link is specifically for 64-bit Linux before compiling the **hl2debug** thing. If your Ubuntu is 32-bit you probably just need **libc6-dev** (which might already be installed).

I have never used hl2debug since Steam and TF2 have worked fine for me since late beta in January, other than minor occasional issues during various TF2 updates.

What video drivers are you running? For nvidia Steam recommends most recent nvidia "experimental" drivers (installed from **Additional Drivers**). What is the output from: dpkg-query -l nvidia* | grep ii
For me in 12.04 it is```
ii  nvidia-common                          1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  nvidia-experimental-310                310.14-0ubuntu0.3                       Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings-experimental-304       304.48-0ubuntu0.1                       Tool of configuring the NVIDIA graphics driver
```

---

### Post by Hydera5 on 2013-07-03
> **efflandt said:**
> Are you running 32-bit or 64-bit Ubuntu? Steam was 32-bit. Not sure if anything in it is 64-bit yet, but it runs fine in 64-bit 12.04 with 32-bit libs (**ia32-libs** package). The **libc6-dev-i386** in that link is specifically for 64-bit Linux before compiling the **hl2debug** thing. If your Ubuntu is 32-bit you probably just need **libc6-dev** (which might already be installed).

I have never used hl2debug since Steam and TF2 have worked fine for me since late beta in January, other than minor occasional issues during various TF2 updates.

What video drivers are you running? For nvidia Steam recommends most recent nvidia "experimental" drivers (installed from **Additional Drivers**). What is the output from: dpkg-query -l nvidia* | grep ii
For me in 12.04 it is```
ii  nvidia-common                          1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  nvidia-experimental-310                310.14-0ubuntu0.3                       Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings-experimental-304       304.48-0ubuntu0.1                       Tool of configuring the NVIDIA graphics driver
```

im 32 bit, heres what i got when i ran what you mentioned earlier:

ii  nvidia-common                             1:0.2.71.1                                i386         transitional package for ubuntu-drivers-common
ii  nvidia-current                            304.88-0ubuntu0.1                         i386         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                           304.88-0ubuntu0.2                         i386         Tool for configuring the NVIDIA graphics driver

---

### Post by efflandt on 2013-07-05
Find "Additional Drivers", which is either in System Settings (gear in Unity bar) or in some versions it was in the gear in upper right corner of screen. "Activate" the most recent experimental one which says something like:

**NVIDIA accelerated graphics driver (**experimental**beta) (version experimental-310)**

Or whatever is the most recent experimental driver at the bottom of the list. I don't know if that will help your issue, but the most recent experimental driver is what Steam recommends for nvidia. In a version of Ubuntu newer than 12.04 the complete driver version number may differ from what mine is.

---

