---
title: "What setup for Steam (not working) for combo Intel/Nvidia?"
date: 2013-11-16
forum: Gaming &amp; Leisure
---

### Post by efflandt on 2013-11-16
My desktop PC is i5 650 with GTX 550 Ti running 64-bit Ubuntu 12.04 and steam works fine on that. It is using nvidia-experimental-310 which is actually 319.32

I got an MSI GE60 20E-073US gaming laptop for travelling which has i7 with both integrated Intel graphics and GTX 765M. It had a Windows D: partition, so I installed 64-bit 13.10 on that because I heard that would have best support for the dual graphics. However, it is unable to run 32-bit graphics tests or steam (which is 32-bit) because it cannot find libGL.so.1 even though those are scattered in numerous locations for 32 and 64-bit libs. It is able to use both graphics for 64-bit apps which I can tell from its power LED which is blue for Intel and amber for Nvidia (when using optirun). I cannot recall if I was able to get primusrun to work for anything, but I know nothing about the dual graphics yet. I tried installing nvidia-prime, but after rebooting it got stuck at a dialog asking if I wanted to run low graphics mode or modify graphics config, but there was no cursor and dialog was unresponsive to keyboard, so I had to go to a console to purge nvidia-prime and reboot.

Is there anything that explains how to set up the dual graphics to be able to run steam and steam games (or different Ubuntu version)?```
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 3D controller: NVIDIA Corporation GK106M [GeForce GTX 765M] (rev ff)

efflandt@MSI-GE60:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-310-updates                        319.60-0ubuntu1                         amd64        Transitional package for nvidia-310-updates
ii  nvidia-319-updates                        319.60-0ubuntu1                         amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                             1:0.2.83                                amd64        transitional package for ubuntu-drivers-common
ii  nvidia-experimental-310                   310.44-0ubuntu2                         amd64        Transitional package for nvidia-experimental-310
ii  nvidia-settings-319-updates               319.60-0ubuntu1                         amd64        Tool for configuring the NVIDIA graphics driver

efflandt@MSI-GE60:/opt/VirtualGL/bin$ ./glxspheres
./glxspheres: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

efflandt@MSI-GE60:/opt/VirtualGL/bin$ optirun ./glxspheres
./glxspheres: error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory

efflandt@MSI-GE60:/opt/VirtualGL/bin$ primusrun ./glxspheres
./glxspheres: error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory

efflandt@MSI-GE60:/opt/VirtualGL/bin$ ./glxspheres64
Polygons in scene: 62464
Visual ID of window: 0x12c
Context is Direct
OpenGL Renderer: Gallium 0.4 on llvmpipe (LLVM 3.3, 256 bits)
24.204554 frames/sec - 27.012283 Mpixels/sec
24.591159 frames/sec - 27.443734 Mpixels/sec
24.307774 frames/sec - 27.127476 Mpixels/sec
24.343246 frames/sec - 27.167062 Mpixels/sec
24.697932 frames/sec - 27.562892 Mpixels/sec
24.620147 frames/sec - 27.476084 Mpixels/sec

efflandt@MSI-GE60:/opt/VirtualGL/bin$ optirun ./glxspheres64
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GTX 765M/PCIe/SSE2
126.164683 frames/sec - 140.799786 Mpixels/sec
125.970612 frames/sec - 140.583203 Mpixels/sec
125.911667 frames/sec - 140.517420 Mpixels/sec
125.438392 frames/sec - 139.989245 Mpixels/sec
125.969220 frames/sec - 140.581649 Mpixels/sec
126.618767 frames/sec - 141.306545 Mpixels/sec

efflandt@MSI-GE60:/opt/VirtualGL/bin$ primusrun ./glxspheres64
Polygons in scene: 62464
Visual ID of window: 0x12c
Segmentation fault (core dumped)

Attempting to run steam (which has not successfully run yet), which this time updated:
[2013-11-15 21:19:17] Downloading Update...
[2013-11-15 21:19:17] Checking for available update...
[2013-11-15 21:19:19] Download Complete.
[2013-11-15 21:19:19] uninstalled manifest found in /home/efflandt/.local/share/Steam/package/steam_client_ubuntu12 (1).
[2013-11-15 21:19:19] Extracting package...
[2013-11-15 21:19:25] Installing update...
[2013-11-15 21:19:25] Cleaning up...
[2013-11-15 21:19:25] Update complete, launching...
[2013-11-15 21:19:25] Shutdown
Restarting Steam by request...
Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME has been set by the user to: /home/efflandt/.local/share/Steam/ubuntu12_32/steam-runtime
Error: You are missing the following 32-bit libraries, and Steam may not run:
libGL.so.1
Installing breakpad exception handler for appid(steam)/version(1383158641_client)
Installing breakpad exception handler for appid(steam)/version(1383158641_client)
[2013-11-15 21:20:01] Startup - updater built Oct 30 2013 11:07:41
[2013-11-15 21:20:01] Verifying installation...
[2013-11-15 21:20:01] Verification complete
[2013-11-15 21:20:05] Shutdown
```

---

### Post by dannyboy79 on 2013-11-18
im going to assume you googled your problem and found this solution? [http://askubuntu.com/questions/260813/trying-to-install-steam-error-you-are-missing-the-following-32-bit-libraries-a](http://askubuntu.com/questions/260813/trying-to-install-steam-error-you-are-missing-the-following-32-bit-libraries-a)

---

### Post by efflandt on 2013-11-19
Thanks, I had not seen that. I was not quite sure what I was searching for and forum and internet searches generated much irrelevant info to weed through.

Even that link was not 13.10 specific, but the 3rd answer seems to have done the trick. Instead of gksu gedit I used "sudo nano /etc/ld.so.conf.d/steam.conf" (which did not exist), added:```
/usr/lib32
/usr/lib/i386-linux-gnu/mesa
```and ran "sudo ldconfig". That worked and steam was able to run.

I then "sudo cp steam.conf glxspheres.conf" from /etc/ld.so.conf.d, but glxspheres still could not find libGLU.so.1 or when using optirun could not find libXv.so.1. So I had to install **libglu1-mesa:i386** and **libxv1:i386** and then those worked. Although, ./glxspheres is slower than ./glxspheres64, optirun ./glxspheres is just as fast as optirun ./glxspheres64.

PS: Launching tf2 from steam with default Intel video was so slow that sounds repeated in little cycles until the next sound. Launching **optirun steam** ran steam with nvidia graphics, and tf2 appeared to be using nvidia from terminal messages, but would immediately core dump. Once I found the following (from back in Feb.) to enter in launch parameters for tf2, I could start steam just using Intel and then tf2 using nvidia:```
LD_PRELOAD="libpthread.so.0 libGL.so.1" _GL_THREADED_OPTIMIZATIONS=1 optirun %command%
```Note that "%command%" is literal for an automatic substitution, not something that you need to substitute with an actual command.

---

