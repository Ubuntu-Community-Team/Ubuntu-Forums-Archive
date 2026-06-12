---
title: "Logitech, Inc. QuickCam Express"
date: 2005-08-06
forum: Desktop Environments
---

### Post by felixdzerzhinsky on 2005-08-06
I am getting the following error when doing: ./quickcam.sh


I am following this thread: [http://www.ubuntuforums.org/showthread.php?t=53755&highlight=logitech+webcam](http://www.ubuntuforums.org/showthread.php?t=53755&highlight=logitech+webcam)


gcc version: gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
gcc version: gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
Make version: GNU Make 3.80
Linker version: GNU ld version 2.15
Kernel compiler: gcc version 3.3.5 (Debian 1:3.3.5-6ubuntu1)
[!] Kernel compiler and gcc seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
        export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels (kgcc is often used in Red Hat systems).
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.

How do I fix this?

---

### Post by felixdzerzhinsky on 2005-08-06
Result of cat /proc/version
Linux version 2.6.10-2-686 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-6ubuntu1)) #1 Thu Jan 27 13:39:43 UTC 2005

lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 001 Device 004: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 001 Device 001: ID 0000:0000

---

### Post by varunus on 2005-08-06
Did you try pressing enter?  It might still work, since both are on gcc3.35.  The one you have on your system is bugfixed a little, that's all.

---

### Post by felixdzerzhinsky on 2005-08-06
Tried that. Errors noted:

awk: cmd. line:1: fatal: cannot open file `/lib/modules/2.6.10-2-686/build/include/linux/version.h' for reading (No such file or directory

 Multiple kernel versions specified in linux/version.h

I can find the following probably compatible devices:
Bus 001 Device 004: ID 046d:0870 Logitech, Inc. QuickCam Express

---

### Post by varunus on 2005-08-06
Do you have the linux-headers package for your kernel installed from synaptic?  You need it to build new modules like you're trying to do.

---

### Post by felixdzerzhinsky on 2005-08-07
Yes I have them. Actually today after rebooting I found that the ./quickcam.sh script is running but my camera still does not work:

You decided to do it, here we go...
=== Leaving root mode ===
The driver detected the following supported cameras:
quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.3 $Date: 2005/04/15 19:32:49 $)
quickcam: Kernel:2.6.10-5-686 bus:1 class:FF subclass:FF vendor:046D product:0870
quickcam: Sensor HDCS-1020 detected
quickcam: Registered device: /dev/video0
I will be using /dev/video0, if there are more cameras I'll not test them.
Press Ctrl+C to quit, Enter to continue --->

Testing if /dev/video0 is correct.
crw-rw----  1 root video 81, 0 2005-08-07 17:17 /dev/video0

Right now driver is loaded and should be ready to run.
Let's test if user applications can see it, starting with qcset.
Press Ctrl+C to quit, Enter to continue --->

Name          : Logitech QuickCam USB
If you like, you can quit now and start using the camera -
you have good chances that it works, if no problems were detected.
If you have X Window System running and xawtv installed,
I can now run it automatically for you.
You will then also have opportunity to install the driver permanently.
Press Ctrl+C to quit, Enter to continue --->

Launching xawtv (press q on xawtv window to quit it)...
If the image is not sharp, try focusing it by turning the
wheel around the camera lens.
        xawtv -noscale -noxv -c "/dev/video0"
This is xawtv-3.94, running on Linux/i686 (2.6.10-5-686)
WARNING: v4l-conf is compiled without DGA support.
/dev/video0 [v4l]: no overlay support
v4l-conf had some trouble, trying to continue anyway
ioctl: VIDIOC_QUERYCAP(driver="";card="";bus_info="";version=0.0.0;capabilities=0x0 []): Unknown error 515
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-lucidatypewriter-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,           -*-courier-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,   -gnu-unifont-bold-r-normal--16-*-*-*-c-*-*-*,        -efont-biwidth-bold-r-normal--16-*-*-*-*-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-m-*-*-*,               -*-*-bold-r-normal-*-16-*-*-*-c-*-*-*,                         -*-*-*-*-*-*-16-*-*-*-*-*-*-*,*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found


Well, did it work, did you get a picture?  Felixdz's comment "The Answer was no :("
If you did, you might now want to install the driver
permanently. Just proceed to do that...
Press Ctrl+C to quit, Enter to continue --->

---

### Post by felixdzerzhinsky on 2005-08-07
Not sure what happened here. In the end I ran the script and ignored all the errors. 

Did **modprobe quickcam** (as root) or you could **sudo modprobe quickcam **also.

Then **sudo gedit /etc/modules** 

That seems to have done it.

Thanks to those who gave advice here and on #ubuntu irc.

---

