---
title: "Very latest NVIDIA packages"
date: 2009-06-06
forum: Desktop Environments
---

### Post by zolero on 2009-06-06
**Hi all!**

I have just finished to build the very latest NVIDIA drivers (most recent three versions) native Hardy packages, for all variants of that distro version. (Not sure if they work on Ibex or Jaunty. I can add support on request, but I don't promise anything...)

Packages can be downloaded by clicking eighter of the links below (RapidShare - sorry, but I haven't any other uploadspace, and hey! that's free...). Before downloading and using them, please **read the rest of the post**. It contains **important** informations.

[nvidia-driver_180.51_zolerubuntu1_i386.deb]("http://rapidshare.com/files/241487984/nvidia-driver_180.51_zolerubuntu1_i386.deb")

[nvidia-source_180.51_zolerubuntu1_all.deb]("http://rapidshare.com/files/241489446/nvidia-source_180.51_zolerubuntu1_all.deb")

[nvidia-driver_180.60_zolerubuntu1_i386.deb]("http://rapidshare.com/files/241555770/nvidia-driver_180.60_zolerubuntu1_i386.deb")

[nvidia-source_180.60_zolerubuntu1_all.deb]("http://rapidshare.com/files/241612027/nvidia-source_180.60_zolerubuntu1_all.deb")

[nvidia-driver_185.18.14_zolerubuntu1_i386.deb]("http://rapidshare.com/files/241612975/nvidia-driver_185.18.14_zolerubuntu1_i386.deb")

[nvidia-source_185.18.14_zolerubuntu1_all.deb]("http://rapidshare.com/files/241613263/nvidia-source_185.18.14_zolerubuntu1_all.deb")

**Driver packages** installing the userspace part of the driver (NVIDIA GLX X-Server libraries,  with CUDA and VDPAU support) and the **nvidia-settings** desktop utility. You'll find also several **xorg.conf** example files in each package's documentation part (**/usr/share/doc** folder).

Please note, that I've **worked around the conflicts** with Mesa GLX an X-Sever's native GLX core in an unconventional way (using the package scripts, but no debian diversions). This is the reason why I am unsure if they will work or not on other distro versions too, since conflicting packages/files may have improved versions, which doesn't match my scripts behaviour. Maybe they could be tried on Ibex (???).

**Source packages** providing the kernel module sources to be compiled for your running kernel. Without that module, the userspace driver part is **useless**. Also one can try out very risky tricks, by using the driver part with other module... Well that's a possibility, but I discourage it definitely. Anyway, the kernel module build and install is very simple, in just few steps, as follows.

Note that **you need** to install the **kernel headers** and the configured **kernel source** for your running kernel, in order to be able to build the module. Therefore here are all necessary steps (preparation, build and install):

Preparing requirements (can be skipped, if you're positive that you already have them):
```
$ sudo apt-get install linux-headers-'uname -r' linux-source-'uname -r'
```Installing the module source package:
```
$ sudo dpkg -i nvidia-source_185.18.14_zolerubuntu1_all.deb
```Changing to the source dir:
```
$ cd /usr/src/nvidia-185.18.14
```Build module:
```
$ sudo make module
```Install module:
```
$ sudo make install
```Insert module into running kernel:
```
$ sudo modprobe nvidia.ko
```Resolving any module dependencies:
```
$ sudo depmod -aq 'uname -r'
```

Now you're on the wave, man! Just install the driver part, and restart your box...

---

### Post by kpkeerthi on 2009-06-07
> **zolero said:**
> 
Packages can be downloaded by clicking eighter of the links below (RapidShare - sorry, but I haven't any other uploadspace, and hey! that's free...).

Have you heard about [Personal Package Archives for Ubuntu]("https://launchpad.net/ubuntu/+ppas") ?

---

