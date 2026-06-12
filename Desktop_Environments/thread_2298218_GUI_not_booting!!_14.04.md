---
title: "GUI not booting!! 14.04"
date: 2015-10-09
forum: Desktop Environments
---

### Post by LocoMotor101 on 2015-10-09
No graphics at all.  When I boot it goes into terminal.  If I type startx, it freezes. The only way to starts the gui is by going to recovery mode. Since I could not find any previous cases similar to mine, I decided to upgrade to 14.04.  But to my surprise the exact same problem continues.  I have no GUI, and when I get it to run, I cannot get the VGA mirror to work.  PLEASE HELP!!

---

### Post by shutterfoot on 2015-10-12
What's your gpu?

---

### Post by LocoMotor101 on 2015-10-13
Sorry for my ignorance shutterfoot, but I do not know what you mean by "gpu." Can you please elaborate on the meaning of that acronysm?  And thanks for taking your time to assist me.

---

### Post by yancek on 2015-10-13
You can get detailed info on your system with the command below and post it here:

```
inxi -b 
```

---

### Post by LocoMotor101 on 2015-10-13
This is the info:

> System:    Host: TOSHI Kernel: 3.13.0-65-generic x86_64 (64 bit) Desktop: Gnome 3.10.4 Distro: Ubuntu 14.04 trusty
Machine:   System: TOSHIBA (portable) product: Satellite C855 version: PSC72U-015006
           Mobo: TOSHIBA model: Portable PC version: MP Bios: Insyde version: 1.60 date: 04/20/2012
CPU:       Dual core Intel Core i3-2370M CPU (-HT-MCP-) clocked at 800.00 MHz 
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller 
           X.Org: 1.15.1 driver: vesa Resolution: 1366x768@0.0hz 
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits) GLX Version: 2.1 Mesa 10.1.3
Network:   Card-1: Realtek RTL8188CE 802.11b/g/n WiFi Adapter driver: rtl8192ce 
           Card-2: Qualcomm Atheros AR8162 Fast Ethernet driver: alx 
Drives:    HDD Total Size: 640.1GB (17.9% used)
Info:      Processes: 213 Uptime: 2:41 Memory: 1469.8/3877.4MB Client: Shell (bash) inxi: 1.9.17 

---

### Post by shutterfoot on 2015-10-14
A few questions if I may? Which version were you upgrading from, and do you remember what preceded the problem? Do you have an xorg.conf file in /etc/X11/? In my past that file has been the cause of many display issues. It shouldn't be a driver issue since you are on intel graphics (same card as mine too). If you have a xorg.conf file there, you should be able to delete it, as a faulty configuration can cause the problems you are seeing. Remember to backup the file first if you think you may want it in the future, but it's no longer needed in recent Ubuntu releases unless you want certain customizations.

Oh.. and i notice you are using the vesa vs the intel graphic driver, and gallium glx instead of mesa. Is that custom? For example, this is what I see: 
```
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller 
           X.Org: 1.16.0 drivers: intel (unloaded: fbdev,vesa) Resolution: 1360x768@60.0hz 
           GLX Renderer: Mesa DRI Intel Sandybridge Desktop GLX Version: 3.0 Mesa 10.3.2


```

---

### Post by LocoMotor101 on 2015-10-14
I upgraded from 12.04 to 14.04.  But, the problem started before that, and to my surprise it was not fixed with the upgrade. It all started when I was erasing "un-necessary" files (I think in /home), which obviously some were. Now, let me add that I also have another smaller partition in this computer also with 14.04 and it all works fine.  I also run windows7 and works also fine. So, the hardware if good. I was hoping to copy the appropriate files from one ubuntu partition to my main one, but I have no idea what to copy.  So, after trying and reading many different threads and not finding a solution, I decided to cry for help!!  Now, I do have xorg.conf.failsafe but not xorg.conf. So, since there is nothing for me to delete, what else you think I should do?

---

### Post by shutterfoot on 2015-10-14
Since you have a working version on your system too, I would try putting the command from above into the working Ubuntu installation and see what driver does it say it's loading for your graphic card. If the driver is our problem we can generate a xorg.conf file telling it to load the proper driver for your graphics then.  On another note, do you have it set to automatically log you in, or should you see a login screen?

---

### Post by LocoMotor101 on 2015-10-14
Well, this is what the other (good) partition indicates.
> System:    Host: toshi Kernel: 3.13.0-65-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: TOSHIBA (portable) product: Satellite C855 version: PSC72U-015006
           Mobo: TOSHIBA model: Portable PC version: MP Bios: Insyde version: 1.60 date: 04/20/2012
CPU:       Dual core Intel Core i3-2370M CPU (-HT-MCP-) clocked at 800.00 MHz 
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller 
           X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@60.0hz 
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile GLX Version: 3.0 Mesa 10.1.3
Network:   Card-1: Realtek RTL8188CE 802.11b/g/n WiFi Adapter driver: rtl8192ce 
           Card-2: Qualcomm Atheros AR8162 Fast Ethernet driver: alx 
Drives:    HDD Total Size: 640.1GB (0.8% used)
Info:      Processes: 208 Uptime: 4 min Memory: 570.3/3877.4MB Client: Shell (bash) inxi: 1.9.17 
Shutterfoot, I can see that the graphics are different in each partition. Is there a way to just simply copy "something" from the good partition to my main partition?  Or do I have to generate the xorg file?  In reference to your question, yes in both partitions the log-in screen appear, but they both look different.  By the way, they used to be the same but about 6 days ago the main partition appeared all different and I have no idea how things work anymore.  I also want to restore the screen that says "Ubuntu Desktop" on the upper left corner.  Thanks.

---

### Post by shutterfoot on 2015-10-14
The login screen does appear! The gui correct? Then you log in and instead of getting a desktop it sends you to a terminal? If that is indeed the case, you should try creating a new user to see if it is as you suspected something in your home directory that is causing the problem.

When you ran the command we've been looking at were you under safe mode? If so, that may be why it loaded vesa instead of intel drivers too.

---

### Post by LocoMotor101 on 2015-10-14
Shutterfoot, no, the gui does not start.  It sends me to terminal.  If I type startx, then it freezes.  So, the only way I can get this gui running is by going to "safe" mode.  Then I start in "normal mode," then hit OK, and the gui starts; and, finally I can log in.  I am going to create a new user and see how it reacts.  More later.

---

### Post by LocoMotor101 on 2015-10-15
Hi Shutterfoot!  I realized that creating another user does not solve anything because the problem starts before I can log onto any user account.  So, there has to be another way to figure out the problem.  Comparing both partition's X11 files, they are both the same, and none has the xorg.conf file.  So, I assume the problematic difference takes place in some other start up  configuration file. So, can you please guide me to where the graphic start up files are located?  Thanks.

---

### Post by shutterfoot on 2015-10-15
Sorry, I misunderstood about the login screen you were seeing. So back to the driver issue. I took a look in (what i believe to be) the Xorg configuration folder at /usr/share/X11/xorg.conf.d, but only see things relating to input devices, no graphics. So I'm unable to suggest any place for a simple copy and paste. Maybe someone more knowledgeable about the modern Xserver could help with that. The best I can do if you want a simple copy and paste try copying this into a text file and save in /etc/X11 as xorg.conf.
```

Section "Device"
    Identifier  "Card0"
    Driver      "intel"
EndSection

```
This should get X to load the proper intel driver for your card. Or you can generate an xorg.conf file by navigating into /ect/X11/ and entering ```
X -configure
``` as super user, which should result in an xorg.conf file. Then of course replace the vesa driver in the device section with intel, like above. I'm still clueless as to why X is using vesa instead of the intel drivers for your device though.. Unless you ran the command in safe mode, and perhaps Ubuntu loads vesa as a safemode driver, then maybe the problem is something else... 

If the above doesn't work for you try posting a log of what happens when you try to load Ubuntu normally. The log should be found at /var/log/Xorg.0.log or some variation of that (for instance if you reboot in safemode to post, then it might be the log created prior to the one most recently there, such as Xorg.1.log). Look for the one that will presumably have errors in it.

---

### Post by shutterfoot on 2015-10-15
you should probably make sure you ran the command in the regular session before trying any of that though, because if it is only loading the vesa driver in safemode, then this won't do any good either.

---

### Post by LocoMotor101 on 2015-10-16
I started in normal mode, and when it ended up in terminal this what the inxi command indicated:
```

Graphics: X.org: 1.15.1 dirver: FAILED vesa tty size: 170x48 Advanced Data: N/A out of X
```

Then, I generated the xorg.conf file and made sure it had the intel driver included.  I tried normal startup but the gui did not start.  So no advance.  Any other idea or clue?  Thanks

---

### Post by deadflowr on 2015-10-16
By no gui, do you mean no graphical login screen?

If so, what is the output for
```
apt-cache policy lightdm
```
and
```
apt-cache policy unity-greeter
```
if nothing, then try installing those, or try reinstalling those if they do exist.

or try reconfiguring lightdm
```
sudo dpkg-reconfigure lightdm
```
if by chance you have a secondary display manager installed, such as gdm, the reconfigure command will open an ncurses window and ask you to select which display manager you want to set as the default.

If lightdm is installed and you've run the reconfigure command, then try starting it with
```
sudo start lightdm
```

I'm not sure if any of this will help, hope it does.
and I don't even know if this is where the problem lies.

---

### Post by blm-ubunet on 2015-10-16
If you look at (& post as attachement) your Xorg log file:
/var/log/Xorg.0.log

We will be able to see what is wrong. Or at least see which kernel & kernel options you are/were using.

The **tricky** part is that this log file is transient; exists for that session & we need to see a failed session that is NOT using "safe mode".
So reboot & use normal grub kernel option.
Login to the console.
Copy the log file /var/log/Xorg.0.log to /home/Documents/somefilename.log.txt.
Reboot to safe mode if you need..

Safe mode results in vesa video driver thru' use of "nomodeset" grub kernel cmd option.

---

### Post by LocoMotor101 on 2015-10-16
Deadflowr: Thank you for your input.  These are the results:

```
lightdm:
  Installed: 1.10.5-0ubuntu1.1
  Candidate: 1.10.5-0ubuntu1.1
  Version table:
 *** 1.10.5-0ubuntu1.1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.10.0-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
 
```

```
unity-greeter:
  Installed: 14.04.11-0ubuntu1
  Candidate: 14.04.11-0ubuntu1
  Version table:
 *** 14.04.11-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     14.04.9-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

Well, I reconfigured lightdm and restarted but it went crazy.  I had to cursors and both cursors were "erasing" everything on it pass.  So, I shut down and reboot it.  Normal boot did not work: As it tried to go into graphics (the ubuntu screen with the blinking dots) it closed and went into terminal.  Startx did not work.  I rebooted and tried with "recovery mode," as I have been doing it for the last 3 weeks.  The interesting thing was that "recovery mode" presented the "unity" screen I want to use, but after log in I got the gui I do not know how to use (I think it is gnome).  
At any rate!! Thanks "blm-ubunet" for your input. And yes, you are correct. The xorg file is transient and there is no way I can copy it and past it when it starts in terminal.
   I have a question:  Is there a way to eliminate other desktop systems and just leave "unity" working?  I do no know if I am using the correct names, but I do not want the one that has the "Activities" on the upper left corner.  Thanks.

---

### Post by The_Forgotten_King on 2015-10-16
> **LocoMotor101 said:**
> Sorry for my ignorance shutterfoot, but I do not know what you mean by "gpu." Can you please elaborate on the meaning of that acronysm?  And thanks for taking your time to assist me.
graphics processor unit. aka video/graphics card

---

### Post by LocoMotor101 on 2015-10-16
This is the output from the Xorg.conf.log file after I attempted normal startup and it went into terminal mode.

```
[    26.874]
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    26.874] X Protocol Version 11, Revision 0
[    26.874] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[    26.874] Current Operating System: Linux TOSHI 3.13.0-65-generic #106-Ubuntu SMP Fri Oct 2 22:08:27 UTC 2015 x86_64
[    26.874] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-65-generic root=UUID=b25b3748-51ab-4cf5-8e8f-1a979218b8e2 ro quiet splash vt.handof$
[    26.874] Build Date: 12 February 2015  02:49:29PM
[    26.874] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support)
[    26.874] Current version of pixman: 0.30.2
[    26.874]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    26.874] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.875] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 16 14:36:31 2015
[    26.988] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.998] (==) No Layout section.  Using the first Screen section.
[    26.998] (==) No screen section available. Using defaults.
[    26.998] (**) |-->Screen "Default Screen Section" (0)
[    26.998] (**) |   |-->Monitor "<default monitor>"
[    26.998] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    26.998] (==) Automatically adding devices
[    26.998] (==) Automatically enabling devices
[    26.998] (==) Automatically adding GPU devices
[    26.998] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist. 
[    26.998]    Entry deleted from font path.
[    26.998] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.998]    Entry deleted from font path.
[    26.998] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.998]    Entry deleted from font path.
[    26.998] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.998]    Entry deleted from font path.
[    26.998] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.998]    Entry deleted from font path.
[    26.998] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    26.998] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg//extra-modules,/usr/lib/xorg/modules"
[    26.998] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.998] (II) Loader magic: 0x7fc8d15ead40
[    26.998] (II) Module ABI versions:
[    26.998]    X.Org ANSI C Emulation: 0.4
[    26.998]    X.Org Video Driver: 15.0
[    26.998]    X.Org XInput driver : 20.0
[    26.998]    X.Org Server Extension : 8.0
[    26.998] (II) xfree86: Adding drm device (/dev/dri/card0)
[    27.000] (--) PCI:*(0:0:2:0) 8086:0116:1179:fb20 rev 9, Mem @ 0xb8000000/4194304, 0xb0000000/134217728, I/O @ 0x00004000/64
[    27.000] Initializing built-in extension Generic Event Extension
[    27.000] Initializing built-in extension SHAPE
[    27.000] Initializing built-in extension MIT-SHM
[    27.000] Initializing built-in extension XInputExtension
[    27.000] Initializing built-in extension XTEST
[    27.000] Initializing built-in extension BIG-REQUESTS
[    27.000] Initializing built-in extension SYNC
[    27.000] Initializing built-in extension XKEYBOARD
[    27.000] Initializing built-in extension XC-MISC
[    27.000] Initializing built-in extension SECURITY
[    27.000] Initializing built-in extension XINERAMA
[    27.000] Initializing built-in extension XFIXES
[    27.000] Initializing built-in extension RENDER
[    27.000] Initializing built-in extension RANDR
[    27.000] Initializing built-in extension COMPOSITE
[    27.000] Initializing built-in extension DAMAGE
[    27.000] Initializing built-in extension MIT-SCREEN-SAVER
[    27.000] Initializing built-in extension DOUBLE-BUFFER
[    27.000] Initializing built-in extension RECORD
[    27.000] Initializing built-in extension DPMS
[    27.000] Initializing built-in extension Present
[    27.000] Initializing built-in extension DRI3
[    27.000] Initializing built-in extension X-Resource
[    27.000] Initializing built-in extension XVideo
[    27.000] Initializing built-in extension XVideo-MotionCompensation
[    27.000] Initializing built-in extension SELinux
[    27.000] Initializing built-in extension XFree86-VidModeExtension
[    27.000] Initializing built-in extension XFree86-DGA
[    27.000] Initializing built-in extension XFree86-DRI
[    27.000] Initializing built-in extension DRI2
[    27.000] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    27.000] (II) "glx" will be loaded by default.
[    27.000] (WW) "xmir" is not to be loaded by default. Skipping.
[    27.000] (II) LoadModule: "glx"
[    27.130] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    27.131] (II) Module glx: vendor="X.Org Foundation"
[    27.131]    compiled for 1.15.1, module version = 1.0.0
[    27.131]    ABI class: X.Org Server Extension, version 8.0
[    27.131]    ABI class: X.Org Server Extension, version 8.0
[    27.131] (==) AIGLX enabled
[    27.131] Loading extension GLX
[    27.131] (==) Matched intel as autoconfigured driver 0
[    27.131] (==) Matched intel as autoconfigured driver 1
[    27.131] (==) Matched modesetting as autoconfigured driver 2
[    27.131] (==) Matched fbdev as autoconfigured driver 3
[    27.131] (==) Matched vesa as autoconfigured driver 4
[    27.131] (==) Assigned the driver to the xf86ConfigLayout
[    27.131] (II) LoadModule: "intel"
[    27.131] (WW) Warning, couldn't open module intel
[    27.131] (II) UnloadModule: "intel"
[    27.131] (II) Unloading intel
[    27.131] (WW) Warning, couldn't open module intel
[    27.131] (II) UnloadModule: "intel"
[    27.131] (II) Unloading intel
[    27.131] (EE) Failed to load module "intel" (module does not exist, 0)
[    27.131] (II) LoadModule: "modesetting"
[    27.132] (WW) Warning, couldn't open module modesetting
[    27.132] (II) UnloadModule: "modesetting"
[    27.132] (II) Unloading modesetting
[    27.132] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    27.132] (II) LoadModule: "fbdev"
[    27.132] (WW) Warning, couldn't open module fbdev
[    27.132] (II) UnloadModule: "fbdev"
[    27.132] (II) Unloading fbdev
[    27.132] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    27.132] (II) LoadModule: "vesa"
[    27.132] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    27.132] (II) Module vesa: vendor="X.Org Foundation"
[    27.132]    compiled for 1.15.0, module version = 2.3.3
[    27.132]    Module class: X.Org Video Driver
[    27.132]    ABI class: X.Org Video Driver, version 15.0
[    27.132] (==) Matched intel as autoconfigured driver 0
[    27.132] (==) Matched intel as autoconfigured driver 1
[    27.132] (==) Matched modesetting as autoconfigured driver 2
[    27.132] (==) Matched fbdev as autoconfigured driver 3
[    27.132] (==) Matched vesa as autoconfigured driver 4
[    27.132] (==) Assigned the driver to the xf86ConfigLayout
[    27.132] (II) LoadModule: "intel"
[    27.132] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    27.132] (II) Module vesa: vendor="X.Org Foundation"
[    27.132]    compiled for 1.15.0, module version = 2.3.3
[    27.132]    Module class: X.Org Video Driver
[    27.132]    ABI class: X.Org Video Driver, version 15.0
[    27.132] (==) Matched intel as autoconfigured driver 0
[    27.132] (==) Matched intel as autoconfigured driver 1
[    27.132] (==) Matched modesetting as autoconfigured driver 2
[    27.132] (==) Matched fbdev as autoconfigured driver 3
[    27.132] (==) Matched vesa as autoconfigured driver 4
[    27.132] (==) Assigned the driver to the xf86ConfigLayout
[    27.132] (II) LoadModule: "intel"
[    27.132] (WW) Warning, couldn't open module intel
[    27.132] (II) UnloadModule: "intel"
[    27.132] (II) Unloading intel
[    27.132] (EE) Failed to load module "intel" (module does not exist, 0)
[    27.132] (II) LoadModule: "modesetting"
[    27.132] (WW) Warning, couldn't open module modesetting
[    27.132] (II) UnloadModule: "modesetting"
[    27.133] (II) Unloading modesetting
[    27.133] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    27.133] (II) LoadModule: "fbdev"
[    27.133] (WW) Warning, couldn't open module fbdev
[    27.133] (II) UnloadModule: "fbdev"
[    27.133] (II) Unloading fbdev
[    27.133] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    27.133] (II) LoadModule: "vesa"
[    27.133] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    27.133] (II) Module vesa: vendor="X.Org Foundation"
[    27.133]    compiled for 1.15.0, module version = 2.3.3
[    27.133]    Module class: X.Org Video Driver
[    27.133]    ABI class: X.Org Video Driver, version 15.0
[    27.133] (II) UnloadModule: "vesa"
[    27.133] (II) Unloading vesa
[    27.133] (II) Failed to load module "vesa" (already loaded, 0)
[    27.133] (II) VESA: driver for VESA chipsets: vesa
[    27.133] (++) using VT number 7

[    27.133] vesa: Ignoring device with a bound kernel driver
[    27.133] (WW) Falling back to old probe method for vesa
[    27.133] (EE) Screen 0 deleted because of no matching config section.
[    27.133] (II) UnloadModule: "vesa"
[    27.133] (EE) Device(s) detected, but none match those in the config file.
[    27.133] (EE)
Fatal server error:
[    27.133] (EE) no screens found(EE)
[    27.133] (EE)
 
```

---

### Post by shutterfoot on 2015-10-16
```
    27.131] (II) LoadModule: "intel"
[    27.131] (WW) Warning, couldn't open module intel
[    27.131] (II) UnloadModule: "intel"
[    27.131] (II) Unloading intel
[    27.131] (WW) Warning, couldn't open module intel
[    27.131] (II) UnloadModule: "intel"
[    27.131] (II) Unloading intel
[    27.131] (EE) Failed to load module "intel" (module does not exist, 0)
[    27.131] (II) LoadModule: "modesetting"
[    27.132] (WW) Warning, couldn't open module modesetting
[    27.132] (II) UnloadModule: "modesetting"
[    27.132] (II) Unloading modesetting
[    27.132] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    27.132] (II) LoadModule: "fbdev"
[    27.132] (WW) Warning, couldn't open module fbdev
[    27.132] (II) UnloadModule: "fbdev"
[    27.132] (II) Unloading fbdev
[    27.132] (EE) Failed to load module "fbdev" (module does not exist, 0)
```
That shouldn't be happening. Are the packages installed for xserver-xorg-video-intel and xserver-xorg-video-fbdev and such?

---

### Post by blm-ubunet on 2015-10-16
Appears the intel i965 driver is not installed? Try:
 sudo apt-get install xserver-xorg-video-intel

might as well install this for h/w video decode with VA-API.
sudo apt-get install libva-intel-vaapi-driver vainfo

---

### Post by LocoMotor101 on 2015-10-16
SUCCESS!! I installed what "blm-ubunet" suggested and it worked.  I was able to enter directly in normal mode. **THANKS a million to all contributors!!**  :p

---

