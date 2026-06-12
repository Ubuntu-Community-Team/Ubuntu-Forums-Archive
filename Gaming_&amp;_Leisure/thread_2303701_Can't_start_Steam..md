---
title: "Can't start Steam."
date: 2015-11-20
forum: Gaming &amp; Leisure
---

### Post by eboone on 2015-11-20
I have Ubuntu 14.04 64 bits. Steam worked fine with a driver for msi geforce 520. I upgraded my graphic card to a Geforce gtx 950 and upgraded the nivdiadrivers from the updatescreen to version 352.63.
The card seems working properly. But when I push at the steam-icon nothing happens and it appears not to start anymore....
What did I do wrong? Thanks a lot for helping

---

### Post by eboone on 2015-11-21
I solved this by installing the required NVIDIA-driver that I downloaded from Nvidia. I followed a procedure to install the nvidia driver explained in Askubuntu. It s working fine now!:D

---

### Post by efflandt on 2015-11-21
That is strange. Usually Ubuntu packages work better than and more coordinated with other programs and updates than the driver script directly from nvidia.com, especially for other future updates. Steam works fine for me with nvidia-352 (352.63) package installed using graphics-drivers/ppa, but if you installed Ubuntu 14.04.3 it may have a newer kernel version than I have from originally installing 14.04.1. I have a GTX 750 Ti that has the new Maxwell chip, although the GTX 960 and GTX 950 were released more recently than GTX 750 series, GTX 970, and GTX 980.```
efflandt@XPS-8100-1404:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-352                                            352.63-0ubuntu0.14.04.1                             amd64        NVIDIA binary driver - version 352.63
ii  nvidia-opencl-icd-352                                 352.63-0ubuntu0.14.04.1                             amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       358.09-0ubuntu0~gpu14.04.1                          amd64        Tool for configuring the NVIDIA graphics driver

efflandt@XPS-8100-1404:~$ uname -a
Linux XPS-8100-1404 3.13.0-68-generic #111-Ubuntu SMP Fri Nov 6 18:17:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```In the future if you have a problem with a gui (X) program, try running it from a terminal (**steam** in this case) and see if the terminal gives any meaningful error message.

---

