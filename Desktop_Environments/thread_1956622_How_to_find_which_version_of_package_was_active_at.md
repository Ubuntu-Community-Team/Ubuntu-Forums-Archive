---
title: "How to find which version of package was active at specific date"
date: 2012-04-11
forum: Desktop Environments
---

### Post by qvx on 2012-04-11
I'm currently running Ubuntu 12.04, but I wan't to find what version of nvidia drivers were active for Ubuntu 10.10 in December 2011 or January 2012. I'm talking about "Additional Drivers" (proprietary drivers which are offered to me after a fresh ubuntu install).

I'm having performance issues with Ubuntu 11.10, 12.04 and Mint 12, yet everything was fine with Ubuntu 10.10. On 12.04 maximization of gnome terminal window often takes 15 seconds. After few hours of using the system, scrolling becomes painfully slow. Also on Mint 12 which uses Gnome Shell, sometimes a startup of gnome terminal takes 10 seconds.

Those are three different distributions/versions and two different desktop environments so I'm guessing it must be the drivers. Kernel is also new, but I guess drivers are more likely cause of problems.

I'v straced the gnome-terminal and when a slowdown occurs it is polling socket /tmp/.X11-unix/X0 like so:

```
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC, 0) = 9
connect(9, {sa_family=AF_FILE, path=@"/tmp/.X11-unix/X0"}, 20) = 0
...
poll([{fd=9, events=POLLIN}], 1, -1) = 1 ([{fd=9, revents=POLLIN}])
```
... poll() takes 15 seconds to finish.

I also tried tweaking "vsync", "sync on refresh" on/off, "detect refresh rate" and similar advices from around the web, but nothing helps. I just can't believe that all those distributions are so bad. It must be someting else so I'm hoping that it is the drivers.

Thans,
Tvrtko

---

### Post by qvx on 2012-04-11
Well, I guess the real question is: "How do I install older version of nvidia drivers on Ubuntu 12.04". "Additional Drivers" program only offers latest 295 version and apt-get cannot install older version.

I have nvidia-173 available

```
Package: nvidia-173
Priority: optional
Section: restricted/misc
Installed-Size: 54515
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: nvidia-graphics-drivers-173

```

but I cannot install it

```
$ sudo apt-get install nvidia-173
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-173 : Depends: xorg-video-abi-10 but it is not installable
              Recommends: nvidia-settings but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I have disabled the nvidia proprietary driver and the problems seem to be gone (can't tell after just half hour of use), but I cannot use second monitor (2560x1440). I neeod older binary drivers on Ubuntu 12.04.

---

### Post by qvx on 2012-04-11
The only unresolved dependency was xorg-video-abi-10 so I did:

```
sudo dpkg --force-depends -i nvidia-173_173.14.30-0ubuntu11_amd64.deb
```

but couln't boot afterwards. So I got to recovery boot option and uninstalled nvidia-173

```
sudo dpkg --remove nvidia-173
```

which fixed the boot problem.

I've been fighting this problem for the past three months. I'we had it.

---

### Post by Krytarik on 2012-04-12
> **qvx said:**
> 
```
[..]
The following packages have unmet dependencies:
 nvidia-173 : Depends: xorg-video-abi-10 but it is not installable
              Recommends: nvidia-settings but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
This is the related bug report:

[https://bugs.launchpad.net/bugs/948053](https://bugs.launchpad.net/bugs/948053)

Good luck!

---

