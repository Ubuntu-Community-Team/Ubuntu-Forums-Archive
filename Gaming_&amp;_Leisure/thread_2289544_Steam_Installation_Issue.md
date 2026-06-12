---
title: "Steam Installation Issue"
date: 2015-08-05
forum: Gaming &amp; Leisure
---

### Post by LairdDeimos on 2015-08-05
Alright, so I have an issue while attempting to install Steam on Ubuntu 14.04. I have attempted to use fixes that seemed to fit my issue but they didn't help. When I clicked on the steam icon after installing from the software center I got this issue in the terminal that popped up:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.4)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```
  The tutorials I've used are 1. [http://ubuntuforums.org/showthread.php?t=2242632](http://ubuntuforums.org/showthread.php?t=2242632) & 2. [http://ubuntuforums.org/showthread.php?t=2233005](http://ubuntuforums.org/showthread.php?t=2233005) for reference. The first advanced me to the next missing library, the second changed nothing. After that, an error window pops up saying ```
You are missing the following 32-bit libraries, and Steam may not run:
libGL.so.1
```  Then, Steam still attempts to load and another window pops up saying ```
Fatal Error: Failed to load steamui.so
``` 
I'm new to Linux, but I'm no idiot, so I can handle instructions. I just need you guys to give me some.

---

### Post by LairdDeimos on 2015-08-05
Ok, nope, this fixed it: 
```
sudo apt-get install -y steam
```

---

### Post by efflandt on 2015-08-05
Did you run System Updater before installing steam? I seem to have newer versions of those libs, but not sure if that is because your system has not be updated or if it is because I am using xorg-edgers ppa for a newer version of my nvidia graphics drivers:```
efflandt@XPS-8100-1404:~$ dpkg-query -l libgl1-mesa-glx* | grep ii
ii  libgl1-mesa-glx:amd64                                 10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~trusty amd64        free implementation of the OpenGL API -- GLX runtime
ii  libgl1-mesa-glx:i386                                  10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~trusty i386         free implementation of the OpenGL API -- GLX runtime

efflandt@XPS-8100-1404:~$ dpkg-query -l libglapi-mesa* | grep ii
ii  libglapi-mesa:amd64                                   10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~trusty amd64        free implementation of the GL API -- shared library
ii  libglapi-mesa:i386                                    10.6.3~git20150727+10.6.ccef8901-0ubuntu0ricotz~trusty i386         free implementation of the GL API -- shared library

efflandt@XPS-8100-1404:~$ dpkg-query -l libcheese* | grep ii
ii  libcheese-gtk23:amd64                                 3.10.2-0ubuntu2                                        amd64        tool to take pictures and videos from your webcam - widgets
ii  libcheese7:amd64                                      3.10.2-0ubuntu2                                        amd64        tool to take pictures and videos from your webcam - base library
```Part 1 of that second link:```

sudo apt-get update && sudo apt-get -y upgrade
```should likely really be:```
sudo apt-get update && sudo apt-get dist-upgrade
```Not sure if -y would help or hurt. Instead of assuming yes in some cases it might abort vs. asking without -y.

Read **man apt-get** and note the difference between **upgrade** and **dist-upgrade**. Note that **upgrade** only upgrades existing packages, but does not handle changing dependencies and may hold some updates back. It would be better to use **dist-upgrade** which is smarter about adding new dependencies, but running **Software Updater** should do the same thing.

---

