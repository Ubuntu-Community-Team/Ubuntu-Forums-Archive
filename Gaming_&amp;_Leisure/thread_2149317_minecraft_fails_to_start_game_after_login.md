---
title: "minecraft fails to start game after login"
date: 2013-05-28
forum: Gaming &amp; Leisure
---

### Post by cpuv2 on 2013-05-28
every time i login i get an error report like this
---- Minecraft Crash Report ----
// You're mean.

Time: 5/28/13 9:02 AM
Description: Failed to start game

java.lang.RuntimeException: org.lwjgl.LWJGLException: X Error - disp: 0xffffffffb0de1a78 serial: 92 error: GLXBadContextTag request_code: 153 minor_code: 5
    at org.lwjgl.opengl.Display.destroyContext(Display.java:985)
    at org.lwjgl.opengl.Display.create(Display.java:863)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at net.minecraft.client.Minecraft.a(SourceFile:226)
    at avv.a(SourceFile:56)
    at net.minecraft.client.Minecraft.run(SourceFile:507)
    at java.lang.Thread.run(Thread.java:679)
Caused by: org.lwjgl.LWJGLException: X Error - disp: 0xffffffffb0de1a78 serial: 92 error: GLXBadContextTag request_code: 153 minor_code: 5
    at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:268)
    at org.lwjgl.opengl.LinuxContextImplementation.nReleaseCurrentContext(Native Method)
    at org.lwjgl.opengl.LinuxContextImplementation.releaseCurrentContext(LinuxContextImplementation.java:97)
    at org.lwjgl.opengl.Context.releaseCurrentContext(Context.java:132)
    at org.lwjgl.opengl.Context.destroy(Context.java:245)
    at org.lwjgl.opengl.Context.forceDestroy(Context.java:229)
    at org.lwjgl.opengl.Display.destroyContext(Display.java:983)
    ... 6 more


A detailed walkthrough of the error, its code path and all known details is as follows:
---------------------------------------------------------------------------------------

-- System Details --
Details:
    Minecraft Version: 1.5.2
    Operating System: Linux (i386) version 3.5.0-31-generic
    Java Version: 1.6.0_27, Sun Microsystems Inc.
    Java VM Version: OpenJDK Client VM (mixed mode, sharing), Sun Microsystems Inc.
    Memory: 10803328 bytes (10 MB) / 36659200 bytes (34 MB) up to 1037959168 bytes (989 MB)
    JVM Flags: 1 total; -Xmx1024m
    AABB Pool Size: 0 (0 bytes; 0 MB) allocated, 0 (0 bytes; 0 MB) used
    Suspicious classes: No suspicious classes found.
    IntCache: cache: 0, tcache: 0, allocated: 0, tallocated: 0
    LWJGL: 2.4.2
    OpenGL: ~~ERROR~~ NullPointerException: null
    Is Modded: Probably not. Jar signature remains and client brand is untouched.
    Type: Client (map_client.txt)
    Texture Pack: Default
    Profiler Position: N/A (disabled)
    Vec3 Pool Size: ~~ERROR~~ NullPointerException: null

i also tried downloading LWJGL but that just gave me a black screen on startup.
it works fine on windows so its not my hardware.
my specs are
2GB RAM
intel pentuim 4 processor 2.80Ghz
intel extreme graphics 2
OS type 32-bit

i also tried running it with both openjdk 6 and 7 but still nothing.
does anyone have any ideas?

---

### Post by Toz on 2013-05-28
Looks like a LWJGL issue. Have a look at [minecraftier]("http://ubuntuforums.org/showthread.php?t=2052084") - it might help.

---

### Post by cpuv2 on 2013-05-28
do you know how i open minecraftier it just takes me to the zip files and doesnt open the program

---

### Post by Toz on 2013-05-28
After you extract the contents of the zip file,
> ..... rightclick it [minecraftier file], choose properties
Go to the permissions-tab, then make it executable
Close properties and run by doubleclicking minecraftier


---

### Post by DarkAmbient on 2013-05-30
> **cpuv2 said:**
> do you know how i open minecraftier it just takes me to the zip files and doesnt open the program

Yea, sorry about that. I changed download location to github some time ago without updating mainpost accordingly, its fixed now. 

I think the file already is executable after you've extracted the zip-file. (as my copy probably was that when I pushed it to github) Not sure though, second opinion on that?

So basically download, extract and doubleclick to start

PS. Thanks Toz, for suggesting Minecraftier. :D

---

### Post by cpuv2 on 2013-06-01
minecraft still wont work i have tried minecraftier but i dont know what to do im all out of ideas does anyone have any more suggestions?

---

### Post by regor210 on 2013-06-02
Lets look at your video drivers.

Open a terminal, press ctrl+alt+t all at the same time. Cut and paste the following command into the terminal window minus $. And post what you get.

$ lsb_release -a && lspci -vmk | grep -A 8 -B 2 VGA && lspci | grep VGA && glxinfo | grep -w 'direct\|OpenGL'

---

### Post by cpuv2 on 2013-06-02
dustin@Dimension-3000:~$  lsb_release -a && lspci -vmk | grep -A 8 -B 2 VGA && lspci | grep VGA && glxinfo | grep -w 'direct\|OpenGL' 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

Device:    00:02.0
Class:    VGA compatible controller
Vendor:    Intel Corporation
Device:    82865G Integrated Graphics Controller
SVendor:    Dell
SDevice:    Dimension 3000
Rev:    02
Driver:    i915
Module:    intelfb
Module:    i915
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
dustin@Dimension-3000:~$

---

### Post by cpuv2 on 2013-06-02
i also installed lwjgl 2.9.0 correctly and downloaded oracle java but still same crash

---- Minecraft Crash Report ----
// Ouch. That hurt :(

Time: 6/2/13 10:32 AM
Description: Failed to start game

org.lwjgl.LWJGLException: Could not init GLX
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:61)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:788)
    at org.lwjgl.opengl.DrawableGL.setPixelFormat(DrawableGL.java:61)
    at org.lwjgl.opengl.Display.create(Display.java:846)
    at org.lwjgl.opengl.Display.create(Display.java:757)
    at org.lwjgl.opengl.Display.create(Display.java:739)
    at net.minecraft.client.Minecraft.a(SourceFile:235)
    at avv.a(SourceFile:56)
    at net.minecraft.client.Minecraft.run(SourceFile:507)
    at java.lang.Thread.run(Thread.java:722)


A detailed walkthrough of the error, its code path and all known details is as follows:
---------------------------------------------------------------------------------------

-- System Details --
Details:
    Minecraft Version: 1.5.2
    Operating System: Linux (i386) version 3.5.0-32-generic
    Java Version: 1.7.0_21, Oracle Corporation
    Java VM Version: Java HotSpot(TM) Client VM (mixed mode), Oracle Corporation
    Memory: 414753808 bytes (395 MB) / 517996544 bytes (494 MB) up to 1037959168 bytes (989 MB)
    JVM Flags: 2 total; -Xmx1023M -Xms511M
    AABB Pool Size: 0 (0 bytes; 0 MB) allocated, 0 (0 bytes; 0 MB) used
    Suspicious classes: No suspicious classes found.
    IntCache: cache: 0, tcache: 0, allocated: 0, tallocated: 0
    LWJGL: 2.9.0
    OpenGL: ~~ERROR~~ RuntimeException: No OpenGL context found in the current thread.
    Is Modded: Probably not. Jar signature remains and client brand is untouched.
    Type: Client (map_client.txt)
    Texture Pack: Default
    Profiler Position: N/A (disabled)
    Vec3 Pool Size: ~~ERROR~~ NullPointerException: null

---

### Post by regor210 on 2013-06-02
Could you please run these commands in terminal to install the  mesa-utils so we can test your OpenGL.  Open a terminal, press ctrl+alt+t all at the same time. Cut and paste the following commands into the terminal window one line at a time minus the $.

$ sudo apt-get update
$ sudo apt-get upgrade

$ sudo apt-get install mesa-utils

Now run 

$ lspci -vmk | grep -A 8 -B 2 VGA && lspci | grep VGA && glxinfo | grep -w 'direct\|OpenGL'


Were looking for something like this at the end


direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 210/PCIe/SSE2
OpenGL version string: 3.3.0 NVIDIA 310.44
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:

Yours will say Intel not Nvidia. Please post what you get

Some of the Integrated Graphics i915 were short on ram like 4m or 8m, too low for 3d  rendering in Ubuntu 12.04. You could look in your  BIOS and see, its also a good idea to set your Integrated Graphics shared RAM to the maximum you can while in your BIOS. OpenGL and direct rendering have to be working for 3d gaming to work. 3D support was discontinued in the older Intel Graphics with low ram. I think the cutoff was 16 megs and over was good and 8 megs or less and you are stuck with 2d. Before Unity I had an old dell office computer with Integrated Graphics i915  4m and it did run Minecraft all be it turned down and laggy. It also did this funny x-ray view when looking up underground.

---

### Post by cpuv2 on 2013-06-03
i put 

glxinfo | grep "OpenGL version" into the terminal because some of the commands were not working
and got Error: couldn't find RGB GLX visual or fbconfig

---

### Post by regor210 on 2013-06-03
Let see if we can find out whats wrong with your OpenGL. Please run these commands and post what you get. 

$ LIBGL_DEBUG=verbose glxinfo | grep render

$ less /var/log/Xorg.0.log | grep gl

---

### Post by cpuv2 on 2013-06-04
[    19.146] (II) LoadModule: "glx"
[    19.146] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    19.147] (II) Module glx: vendor="X.Org Foundation"
[    19.906] (II) config/udev: Adding input device HP HP Link-5 micro dongle (/dev/input/event4)
[    19.906] (**) HP HP Link-5 micro dongle: Applying InputClass "evdev keyboard catchall"
[    19.906] (II) Using input driver 'evdev' for 'HP HP Link-5 micro dongle'
[    19.906] (**) HP HP Link-5 micro dongle: always reports core events
[    19.907] (**) evdev: HP HP Link-5 micro dongle: Device: "/dev/input/event4"
[    19.907] (--) evdev: HP HP Link-5 micro dongle: Vendor 0x3f0 Product 0xa407
[    19.907] (--) evdev: HP HP Link-5 micro dongle: Found keys
[    19.907] (II) evdev: HP HP Link-5 micro dongle: Configuring as keyboard
[    19.907] (II) XINPUT: Adding extended input device "HP HP Link-5 micro dongle" (type: KEYBOARD, id 10)
[    19.908] (II) config/udev: Adding input device HP HP Link-5 micro dongle (/dev/input/event5)
[    19.908] (**) HP HP Link-5 micro dongle: Applying InputClass "evdev pointer catchall"
[    19.908] (**) HP HP Link-5 micro dongle: Applying InputClass "evdev keyboard catchall"
[    19.908] (II) Using input driver 'evdev' for 'HP HP Link-5 micro dongle'
[    19.908] (**) HP HP Link-5 micro dongle: always reports core events
[    19.908] (**) evdev: HP HP Link-5 micro dongle: Device: "/dev/input/event5"
[    19.908] (--) evdev: HP HP Link-5 micro dongle: Vendor 0x3f0 Product 0xa407
[    19.908] (--) evdev: HP HP Link-5 micro dongle: Found 9 mouse buttons
[    19.908] (--) evdev: HP HP Link-5 micro dongle: Found scroll wheel(s)
[    19.908] (--) evdev: HP HP Link-5 micro dongle: Found relative axes
[    19.908] (--) evdev: HP HP Link-5 micro dongle: Found x and y relative axes
[    19.908] (--) evdev: HP HP Link-5 micro dongle: Found absolute axes
[    19.908] (II) evdev: HP HP Link-5 micro dongle: Forcing absolute x/y axes to exist.
[    19.908] (--) evdev: HP HP Link-5 micro dongle: Found keys
[    19.908] (II) evdev: HP HP Link-5 micro dongle: Configuring as mouse
[    19.908] (II) evdev: HP HP Link-5 micro dongle: Configuring as keyboard
[    19.908] (II) evdev: HP HP Link-5 micro dongle: Adding scrollwheel support
[    19.908] (**) evdev: HP HP Link-5 micro dongle: YAxisMapping: buttons 4 and 5
[    19.908] (**) evdev: HP HP Link-5 micro dongle: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.908] (II) XINPUT: Adding extended input device "HP HP Link-5 micro dongle" (type: KEYBOARD, id 11)
[    19.909] (II) evdev: HP HP Link-5 micro dongle: initialized for relative axes.
[    19.909] (WW) evdev: HP HP Link-5 micro dongle: ignoring absolute axes.
[    19.909] (**) HP HP Link-5 micro dongle: (accel) keeping acceleration scheme 1
[    19.909] (**) HP HP Link-5 micro dongle: (accel) acceleration profile 0
[    19.909] (**) HP HP Link-5 micro dongle: (accel) acceleration factor: 2.000
[    19.909] (**) HP HP Link-5 micro dongle: (accel) acceleration threshold: 4
[    19.910] (II) config/udev: Adding input device HP HP Link-5 micro dongle (/dev/input/mouse0)
this is what i get when i put the second command the first command i get this
couldn't find RGB GLX visual or fbconfig

---

### Post by regor210 on 2013-06-04
[ 19.146] (II) LoadModule: "glx"
[ 19.146] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 19.147] (II) Module glx: vendor="X.Org Foundation"

This looks good, it found the Modules and loaded them without any errors.
But it not working so try running these commands and post what you get.

$ sudo lshw -C video


If the output of this command is over a page just post the first 10 lines.
$ glxinfo

---

### Post by cpuv2 on 2013-06-04
*-display               
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff ioport:ed98(size=8)
dustin@Dimension-3000:~$ glxinfo 
name of display: :0
Error: couldn't find RGB GLX visual or fbconfig

---

### Post by regor210 on 2013-06-04
I poked around the web and found there's a bug-report for your 82865G Integrated Graphics Controller here.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1071530](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1071530)

askubuntu.com has a solution but it broke at least one person's Ubuntu insulation causing it to boot in to a black screen. So I would backup my system before trying it.

[http://askubuntu.com/questions/263550/opengl-with-intel-82865g-integrated-graphics](http://askubuntu.com/questions/263550/opengl-with-intel-82865g-integrated-graphics)

""Thanks for the link to that bug report, fossfreedom. I hadn't found it. The bug report doesn't state a direct answer, but the answer seems as simple as the following command:""

$ sudo apt-get install xserver-xorg-core

---

### Post by cpuv2 on 2013-06-04
it says i have the newest version of xserver-xorg-core when i try to install it.
btw thank you for all your help and time. I apperciate that your trying to help alot:D[h=3][/h]

---

### Post by regor210 on 2013-06-04
In your BIOS, how many megs does your Integrated Graphics have?
When you first start your computer a message will flash across the screen” press F1 to enter setup” sometimes its not F1 its the Del key. This setup menu is your BIOS.

---

### Post by cpuv2 on 2013-06-05
96MB i saw that on windows. i have a dualboot.

---

### Post by regor210 on 2013-06-05
I was looking over the bug report and it looks like your 3D problem is fixed in Ubuntu 13.04.

I looked into updating your Mesa video drivers but to get  the newer mesa 9.2 driver you would need a 3.6 or newer kernel. The kernel is paired to the software in the redepositors so upgrading to a newer kernel is likely to to fix one problem but make more problems with other things.

So if you can get Ubuntu 13.04 up and running on a live cd/usb and run 

$ glxinfo 

If it works I would recommend installing 13.04 not upgrading as upgrading sometimes brings the problem with it.

One more thing, some times windows video drivers can change the amount of ram used by the Graphics adapter so its likely your shared ram is 96m in your BIOS but it wouldn't hurt to have a look.

---

### Post by cpuv2 on 2013-06-05
i increased my onboard video buffer from 1MB to 8MB that may help. but Minecraft is still crashing.

---

### Post by Cvxcvgg on 2013-06-05
I noticed that your memory in the output from the crash file was 395/494 MB, and I suppose the 494 MB would be the dedicated RAM for your graphics card. If that is correct, you are under the minimum benchmarks for Minecraft, which state that you need 512 MB of RAM for your graphics card. If you have more available memory, you should probably look further into the cause of it being limited, since that number is probably what's causing the crashes.

---

