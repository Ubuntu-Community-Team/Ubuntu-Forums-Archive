---
title: "Wesnoth"
date: 2012-08-21
forum: Gaming &amp; Leisure
---

### Post by TNAFan on 2012-08-21
I attempt to launch Wesnoth, and I recieve the following error:

Battle for Wesnoth v1.10.3
Started on Tue Aug 21 19:23:31 2012

20120821 19:23:31 error display: Could not initialize SDL_video: No available video device
Could not initialize video. Exiting.


Could someone tell me how to fix this?

---

### Post by thatguruguy on 2012-08-21
It would be helpful if you described your hardware, the version of Ubuntu you are running, etc.

---

### Post by synaptix on 2012-08-21
Did a search and found a similar hit via Google here:

[http://ubuntuforums.org/showthread.php?t=944671](http://ubuntuforums.org/showthread.php?t=944671)
(It's an old topic but...)

There seems to be a fix for 12.04, assuming your are running the latest version:

[http://ubuntuforums.org/showpost.php?p=12135216&postcount=5](http://ubuntuforums.org/showpost.php?p=12135216&postcount=5)

---

### Post by TNAFan on 2012-08-21
Running a Dell Inspiron N5050 with Ubuntu 12.04

---

### Post by TNAFan on 2012-08-21
> **synaptix said:**
> Did a search and found a similar hit via Google here:

[http://ubuntuforums.org/showthread.php?t=944671](http://ubuntuforums.org/showthread.php?t=944671)
(It's an old topic but...)

There seems to be a fix for 12.04, assuming your are running the latest version:

[http://ubuntuforums.org/showpost.php?p=12135216&postcount=5](http://ubuntuforums.org/showpost.php?p=12135216&postcount=5)

Didn't work.  It would not allow me to run the "sudo apt-get remove libsdl1.2debian" command.  I got stuck with the error of:

sudo apt-get remove libsdl
libsdl1.2debian  libsdl-image1.2  libsdl-net1.2    libsdl-perl      libsdl-ttf2.0-0
libsdl-gfx1.2-4  libsdl-mixer1.2  libsdl-pango1    libsdl-sound1.2  
justin@beastjr:~$ sudo apt-get remove libsdl1.2debian 
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 testdrive-common : Depends: qemu-kvm but it is not going to be installed or
                             kvm (>= 1:84+dfsg-0ubuntu12.4) or
                             virtualbox-ose (>= 3.1.6) but it is not going to be installed or
                             virtualbox-3.1 but it is not installable or
                             virtualbox-3.2 but it is not installable or
                             virtualbox-4.0 but it is not installable
                    Recommends: kvm-pxe but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

---

### Post by thatguruguy on 2012-08-21
> **TNAFan said:**
> Didn't work.  It would not allow me to run the "sudo apt-get remove libsdl1.2debian" command.  I got stuck with the error of:

sudo apt-get remove libsdl
libsdl1.2debian  libsdl-image1.2  libsdl-net1.2    libsdl-perl      libsdl-ttf2.0-0
libsdl-gfx1.2-4  libsdl-mixer1.2  libsdl-pango1    libsdl-sound1.2  
justin@beastjr:~$ sudo apt-get remove libsdl1.2debian 
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 testdrive-common : Depends: qemu-kvm but it is not going to be installed or
                             kvm (>= 1:84+dfsg-0ubuntu12.4) or
                             virtualbox-ose (>= 3.1.6) but it is not going to be installed or
                             virtualbox-3.1 but it is not installable or
                             virtualbox-3.2 but it is not installable or
                             virtualbox-4.0 but it is not installable
                    Recommends: kvm-pxe but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

Those warnings aren't about the removal of sdl, they mean you have other broken packages. What happens when you type the following in a terminal?
```
sudo apt-get update
```

---

### Post by TNAFan on 2012-08-21
Fetched 1,815 kB in 1min 15s (23.9 kB/s)
Reading package lists... Done
justin@beastjr:~$ 


No errors.

---

### Post by thatguruguy on 2012-08-21
How about 
```
sudo apt-get upgrade
```

---

### Post by thatguruguy on 2012-08-21
How did you install Battle of Wesnoth? Did you get it from the Ubuntu Software Center?

---

### Post by TNAFan on 2012-08-22
> **thatguruguy said:**
> How about 
```
sudo apt-get upgrade
```

No errors.

---

### Post by TNAFan on 2012-08-22
> **thatguruguy said:**
> How did you install Battle of Wesnoth? Did you get it from the Ubuntu Software Center?

Yes I did.

---

### Post by thatguruguy on 2012-08-24
Have you made any changes to your system? It seems like you've deleted/changed your graphics drivers. If you could, open a terminal and type the following:
```
glxgears
```
let it run for a bit, and then post the results here.

---

### Post by TNAFan on 2012-08-24
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
259 frames in 5.0 seconds = 51.720 FPS
299 frames in 5.0 seconds = 59.650 FPS
299 frames in 5.0 seconds = 59.654 FPS
298 frames in 5.0 seconds = 59.453 FPS
299 frames in 5.0 seconds = 59.643 FPS
299 frames in 5.0 seconds = 59.652 FPS
299 frames in 5.0 seconds = 59.655 FPS
299 frames in 5.0 seconds = 59.663 FPS
299 frames in 5.0 seconds = 59.649 FPS
299 frames in 5.0 seconds = 59.653 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 6378 requests (6378 known processed) with 0 events remaining.



Haven't changed any graphics drivers either.

---

### Post by TNAFan on 2012-08-29
bump

---

