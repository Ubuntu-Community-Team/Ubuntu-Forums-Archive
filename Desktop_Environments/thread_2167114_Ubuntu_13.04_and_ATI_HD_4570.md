---
title: "Ubuntu 13.04 and ATI HD 4570"
date: 2013-08-12
forum: Desktop Environments
---

### Post by OssamaNas on 2013-08-12
I have an ASUS X61SL laptop with AMD Mobility Radeon HD 4570 graphic card , Ubuntu 13.04 Raring x86_64
The first time I used the fglrx driver : after restart I was unable to change the display resolution which has been set automatically to 1027*786 more to that the display smeed to zoomed in : no unity dash,no top panel nothing like zoomed in to the middle of the display
After formatting and reinstalling the system I went to AMD website and downloaded the latest version :amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64
And when I tried to install it , it gave this message :
[ATTACH=CONFIG]245320[/ATTACH]
And when I went to check the specified file , I found this :
> Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/3.8.0-27-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.
I have downloaded the kernel 3.8.0.27 headers when I updated my system but I cannot find the file specified
What can I do ?

---

### Post by QIII on 2013-08-12
Moved to its own thread.

Hello, OssamaNas!

Your problem is distinct from the issue being discussed in [http://ubuntuforums.org/showthread.php?t=2166697](http://ubuntuforums.org/showthread.php?t=2166697), so I have moved it to its own thread.

There are several members who will be able to fill you in on your issue.

Best wishes!

---

### Post by Cheesemill on 2013-08-12
Unfortunately the only driver you can use with 13.04 and your graphics card is the open source radeon driver which comes built into Ubuntu.

ATI stopped supporting all 2/3/4xxx series cards on Linux last year so they don't write drivers for them anymore. There isn't a version of flgrx that will work on your setup.

---

### Post by OssamaNas on 2013-08-12
I have an ASUS X61SL laptop with AMD Mobility Radeon 4570 HD
When I install the fglrx from Synaptic Package Manager and restart my laptop
The desktop was set to 1024*768 and I cannot change it, Unity launcher and top panel are not visible at all , but keyboard shortcuts are operational
After using the terminal to launch synaptic and uninstall fglrx and restart
The resolution was back to normal (16" display) but the unity launcher and top panel are not visible and when I tried to launch unity through terminal I lose window border which are actually available (Close,Max and min buttons along with snapping to edges)
What can I do to get everything back right? write know I'm downloading Cinnamon ( which the desktop environment for Mint) to try to get some desktop functionalty back (which I'm not sure if it will work)
Help guys

---

### Post by OssamaNas on 2013-08-12
Cinnamon is a success , the desktop is back to normal
Unity : still no luck

---

### Post by OssamaNas on 2013-08-12
I removed then installed unity : no luck 
I thing the problem lies deep in gnome3 settings not unity itself

---

### Post by QIII on 2013-08-12
Threads merged.

---

