---
title: "Windows manager fails to start Ubuntu 10.10"
date: 2010-12-10
forum: Desktop Environments
---

### Post by kakila on 2010-12-10
Hi all
I tried to update form 10.04 to 10.10 but it was impossible. I decided to do a fresh install of Ubuntu 10.10, but keeping my old /home (which was in a different partition). 
Everything went OK except that the windows manager does not start correctly. Tee symptoms are:
1- Pressing the show desktop button (bottom left corner) produces: "Your window manager does not support the show desktop button, or you are not running a window manager"
2- Windows have no decorations (you cannot close them, minimize them, not move them, etc...)
3- Errors in ~/.xsession-errors (attached)
4- The first time I boted I saw a nice Ubuntu splash screen while loading everything. Now I see a rather crappy "Ubuntu 10.10" and lots of loading info with bad formatting (maybe this gives a clue t somebody).

I tried 
> gnome-appearance-properties

I get 

(gnome-appearance-properties:7283): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7283): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

I tried the solutions in the thread [http://ubuntuforums.org/showthread.php?p=10222652#post10222652](http://ubuntuforums.org/showthread.php?p=10222652#post10222652) but they do not work for me
I am using
libgnome-window-settings1 2.32.0-0ubuntu2
capplets-data 2.32.0-0ubuntu2

I have a NVIDIA GeForce 8400M G and apparently is correctly detected, though I see no NVIDIA splash screen when I boot.

I have the additional drivers installed but compiz is unable to activate the effects (thoug it could the first time I booted).

Thanks for your help!

---

### Post by thebear79 on 2010-12-10
Similar problems here new to Ubuntu any help would be great

Thanks

---

### Post by kakila on 2010-12-15
bump

more info: If I Remove the propietary drivers, reboot, activate the drivers again and reboot, WHEN rebooting the Ubuntu splash window is the beatiful one. When the system boots again, back to the ugly ubuntu arial-like splash screen and no NVidia splash-screen. I think the problem is with the drivers...what can I do? Help!!! :D

Update: I went medieval with xserver and nvidia and uninstalled  nvidia-current nvidia-common nvidia-settings and xserver-xorg-video-all. Booting freezees in the NICE Ubuntu splash screen. Putting xserver back allows log in graphic mode (still booting with good splash screen). As soon as I install the NVidia drivers (graphic card detected correctly!) I got back to the ugly Ubuntu splash screen and my problems start again, no decorations in windows, view desktop button not working, not able to activate nomal level of visual effects. How can I know if there an problem with the drivers? any log file to look at?

Update 2: Got compiz-check:
wget [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download) -O compiz-check
(make it executable)

$ ./compiz-check
Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G86 [GeForce 8400M G] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

$ dmesg | grep nvidia
[   12.840722] nvidia: module license 'NVIDIA' taints kernel.
[   13.811007] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.811018] nvidia 0000:01:00.0: setting latency timer to 64

---

### Post by ingeva on 2010-12-15
When I installed the desktop version of 10.10 I had the same problem.
All I did was to log in from text-mode and updated the system:

sudo apt-get -y dist-upgrade

and at the next boot everything was OK.

(To go to text mode, just type CTRL+Alt+F1).

---

### Post by kakila on 2010-12-16
Thanks for the answer.

I tried, nothing is changed.

Appart for ~/.xsessions-errors is there another file tht can give me a hint?

---

### Post by Raugturi on 2010-12-17
Hey kakila, I have this exact same issue.  Did you find any solution yet?

---

### Post by kakila on 2010-12-17
Nothing yet, still searching for more clues. I would say my drivers are OK, but the Windows Manager is the one having problems...

Will post if I solve it

---

### Post by Krytarik on 2010-12-17
1.) re-install the uninstalled packages

2.) Save the configuration to the "xorg.conf":
- go to "System -> Administration -> NVIDIA X Server Settings"
- click at "X Server Display Configuration" on the left side
- check/choose your desired configuration
- click at "Save to X Configuration File"
- enter your "root"-password when asked
- choose replace, not merge!

3.) If it still doesn't work after that, post the content of "/etc/X11/xorg.conf".

---

### Post by kakila on 2010-12-17
Thanks a lot Krytarik, I had tried similar thing before. The only difference was the last step (I had always merge). However, still the same problem.

Here is the content of "/etc/X11/xorg.conf"

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@palmer)  Mon Oct  4 16:01:38 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M G"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

The only hint to what is wrong is in the ~/.xsessions-errors (this one after I did System->Preferences->Appearance, selected Visual Effects tab and selected Normal, and the system said "Desktop effects could not be enabled", however I got back the decorations of the windows.)

```

Setting IM through im-switch for locale=en_US.
Start IM through /home/juanpi/.xinput.d/en_US linked to /etc/X11/xinit/xinput.d/none.
GNOME_KEYRING_CONTROL=/tmp/keyring-lavs4m
GNOME_KEYRING_CONTROL=/tmp/keyring-lavs4m
SSH_AUTH_SOCK=/tmp/keyring-lavs4m/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-lavs4m
SSH_AUTH_SOCK=/tmp/keyring-lavs4m/ssh

(polkit-gnome-authentication-agent-1:1539): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1539): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: adding killswitch idx 1 state KILLSWITCH_STATE_UNBLOCKED
** Message: killswitch 1 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitches state KILLSWITCH_STATE_UNBLOCKED
** Message: killswitch 1 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitches state KILLSWITCH_STATE_UNBLOCKED
** Message: applet now removed from the notification area
** (nm-applet:1554): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1554): DEBUG: foo_client_state_changed_cb
Initializing nautilus-gdu extension

(nautilus:1545): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** (nm-applet:1554): DEBUG: foo_client_state_changed_cb
Unable to open desktop file /usr/share/applications/kde4/amarok.desktop for panel launcher: No such file or directory
Unable to open desktop file /usr/local/share/applications/google-chrome.desktop for panel launcher: No such file or directory
** Message: applet now embedded in the notification area
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (update-notifier:1786): DEBUG: aptdaemon on bus: 0
** (update-notifier:1786): DEBUG: Skipping reboot required
There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Backend     : ini
Integration : true
Profile     : default
Adding plugins

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Initializing core options...done

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Initializing composite options...done

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Initializing opengl options...done

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Initializing decor options...done
Initializing mousepoll options...done
Initializing scale options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Initializing wall options...done
Initializing ezoom options...done
Initializing staticswitcher options...done
Initializing resize options...done

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Starting gtk-window-decorator

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1757): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

```

---

### Post by Krytarik on 2010-12-17
The settings of your monitor don't look correct to me.

To see what settings your monitor supports, enter "xvidtune" in a terminal, then press cancel.

---

### Post by kakila on 2010-12-17
Output after pressing Cancel (pretty scary!!)

Vendor: Unknown, Model: AUO
Num hsync: 1, Num vsync: 1
hsync range 0:  30.00 -  75.00
vsync range 0:  60.00 -  60.00

BTW, everything worked well in 10.04 and was exactly the same. My guesses: Is either problem with the new version of the NVidia drivers (hope not, hope not!) or there is something left in my /home that is messing everything or preventing things to install correctly.

---

### Post by Krytarik on 2010-12-17
So, the monitor settings are correct.

Which version of the nvidia drivers are you using, have you tried to downgrade them?

---

### Post by kakila on 2010-12-17
> dpkg -l | grep nvidia
ii  nvidia-173-modaliases                173.14.28-0ubuntu1                                Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-96-modaliases                 96.43.18-0ubuntu1                                 Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-common                        0.2.24                                            Find obsolete NVIDIA drivers
ii  nvidia-current                       260.19.06-0ubuntu1                                NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-modaliases            260.19.06-0ubuntu1                                Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-settings                      260.19.06-0ubuntu1                                Tool of configuring the NVIDIA graphics driver

I will try what it said here [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) about removing Nouveau.

Update: Tried "sudo apt-get --purge remove xserver-xorg-video-nouveau" and reboot, nothing changed, same problem.

---

### Post by kakila on 2010-12-17
Checking launchpad I found this bug
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641)
From there I saw the file /var/log/Xorg.0.log
It seems I do not suffer that bug (I think, not sure!). Anyway I am posting the content of the file I what I think is the related chunk.

```
[    18.670] (II) LoadModule: "glx"
[    18.670] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    18.693] (II) Module glx: vendor="NVIDIA Corporation"
[    18.693]    compiled for 4.0.2, module version = 1.0.0
[    18.694]    Module class: X.Org Server Extension
[    18.694] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[    18.694] (II) Loading extension GLX
[    18.694] (II) LoadModule: "record"
[    18.694] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.694] (II) Module record: vendor="X.Org Foundation"
[    18.694]    compiled for 1.9.0, module version = 1.13.0
[    18.694]    Module class: X.Org Server Extension
[    18.694]    ABI class: X.Org Server Extension, version 4.0
[    18.694] (II) Loading extension RECORD
[    18.694] (II) LoadModule: "dri"
[    18.695] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.695] (II) Module dri: vendor="X.Org Foundation"
[    18.695]    compiled for 1.9.0, module version = 1.0.0
[    18.695]    ABI class: X.Org Server Extension, version 4.0
[    18.695] (II) Loading extension XFree86-DRI
[    18.695] (II) LoadModule: "dri2"
[    18.695] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.695] (II) Module dri2: vendor="X.Org Foundation"
[    18.695]    compiled for 1.9.0, module version = 1.2.0
[    18.695]    ABI class: X.Org Server Extension, version 4.0
[    18.695] (II) Loading extension DRI2
[    18.695] (II) LoadModule: "nvidia"
[    18.695] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    18.696] (II) Module nvidia: vendor="NVIDIA Corporation"
[    18.696]    compiled for 4.0.2, module version = 1.0.0
[    18.696]    Module class: X.Org Video Driver
[    18.696] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 06:37:13 PDT 2010
[    18.696] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    18.696] (++) using VT number 7
[    18.698] (II) Loading sub module "fb"
[    18.698] (II) LoadModule: "fb"
[    18.698] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.698] (II) Module fb: vendor="X.Org Foundation"
[    18.698]    compiled for 1.9.0, module version = 1.0.0
[    18.698]    ABI class: X.Org ANSI C Emulation, version 0.4
[    18.698] (II) Loading sub module "wfb"
[    18.698] (II) LoadModule: "wfb"
[    18.699] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    18.699] (II) Module wfb: vendor="X.Org Foundation"
[    18.699]    compiled for 1.9.0, module version = 1.0.0
[    18.699]    ABI class: X.Org ANSI C Emulation, version 0.4
[    18.699] (II) Loading sub module "ramdac"
[    18.699] (II) LoadModule: "ramdac"
[    18.699] (II) Module "ramdac" already built-in
[    18.699] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    18.699] (==) NVIDIA(0): RGB weight 888
[    18.699] (==) NVIDIA(0): Default visual is TrueColor
[    18.699] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    18.699] (**) NVIDIA(0): Option "TwinView" "0"
[    18.699] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
[    18.699] (**) NVIDIA(0): Enabling RENDER acceleration
[    18.699] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    18.699] (II) NVIDIA(0):     enabled.
[    19.767] (II) NVIDIA(0): NVIDIA GPU GeForce 8400M G (G86M) at PCI:1:0:0 (GPU-0)
[    19.767] (--) NVIDIA(0): Memory: 524288 kBytes
[    19.767] (--) NVIDIA(0): VideoBIOS: 60.86.38.00.36
[    19.767] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    19.767] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    19.767] (--) NVIDIA(0): Connected display device(s) on GeForce 8400M G at PCI:1:0:0
[    19.767] (--) NVIDIA(0):     AUO (DFP-0)
[    19.767] (--) NVIDIA(0): AUO (DFP-0): 330.0 MHz maximum pixel clock
[    19.767] (--) NVIDIA(0): AUO (DFP-0): Internal Dual Link LVDS
[    19.810] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    19.811] (II) NVIDIA(0): Validated modes:
[    19.811] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[    19.811] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[    20.828] (--) NVIDIA(0): DPI set to (110, 108); computed from "UseEdidDpi" X config
[    20.828] (--) NVIDIA(0):     option
[    20.828] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    20.828] (--) Depth 24 pixmap format is 32 bpp
[    20.828] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    20.830] (II) NVIDIA(0): Initialized GPU GART.
[    20.835] (II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
[    20.835] (II) NVIDIA(0):     enough to receive ACPI hotkey events.
[    20.835] (II) NVIDIA(0): ACPI brightness change hotkey events enabled.
[    20.840] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[    21.168] (II) Loading extension NV-GLX
[    21.193] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    21.216] (==) NVIDIA(0): Disabling shared memory pixmaps
[    21.216] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    21.216] (==) NVIDIA(0): Backing store disabled
[    21.216] (==) NVIDIA(0): Silken mouse enabled
[    21.225] (**) NVIDIA(0): DPMS enabled
[    21.225] (II) Loading extension NV-CONTROL
[    21.226] (II) Loading extension XINERAMA
[    21.226] (II) Loading sub module "dri2"
[    21.226] (II) LoadModule: "dri2"
[    21.226] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.226] (II) NVIDIA(0): [DRI2] Setup complete

```

---

### Post by Krytarik on 2010-12-17
Your home-directory doesn't affect the installation of packages/drivers.  But it is affecting the Compiz-settings! Thus you could create another user, and  try it again with the new profile.

So, you have the version 260 running. Go into Synaptic, search for "nvidia" (Name), right-click at the respective packages, click on "Properties" and click on the tab "Version" to check if there is an earlier version available, I can't check it here, running 10.04.
If so, click in the menu at "Package", then "Force Version".

EDIT: As for the bug you mentioned, I don't see any parallels. Also I am running proprietary drivers (version 96) with my Nvidia-card and have no problems.

---

### Post by kakila on 2010-12-17
Thanks again,

I will try with the new user tomorrow.

I check the version of the drivers and 260 is the only one. I cannot Force version...

It called my attention that the optional package nvidia-kernel-common is not install. Could it make any differences. 

From the previous post I not ethat glx looks to be OK, nevertheless in the ~/.xsession-errors it fails to do something...

---

### Post by kakila on 2010-12-17
Found this bug... in 11.04 (??) 
Related?

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/689144](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/689144)

---

### Post by Krytarik on 2010-12-17
> **kakila said:**
> Thanks again,

I will try with the new user tomorrow.

I check the version of the drivers and 260 is the only one. I cannot Force version...

It called my attention that the optional package nvidia-kernel-common is not install. Could it make any differences. 

From the previous post I not ethat glx looks to be OK, nevertheless in the ~/.xsession-errors it fails to do something...
The package "nvidia-kernel-common" will not get installed by default, obviously, I don't have it either, these are my packages:```

ii  nvidia-173-modaliases                 173.14.22-0ubuntu11                             Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96                             96.43.17-0ubuntu1                               NVIDIA binary Xorg driver, kernel module and
ii  nvidia-96-modaliases                  96.43.17-0ubuntu1                               Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                         0.2.23                                          Find obsolete NVIDIA drivers
ii  nvidia-current-modaliases             195.36.24-0ubuntu1~10.04                        Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-settings                       195.36.08-0ubuntu2                    
```As of the description you could also install the version 173, instead of 260.

But you may try another way (they also offer Nvidia-drivers):
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Ubuntu_X_Team.27s_PPA](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Ubuntu_X_Team.27s_PPA)

As for the error-messages in xsession-errors: I also get some as well, even if everything seems to work fine. But there are some more in your log, thus I would definetely try the new-user-thing.

EDIT: About the bug: It could be the same issue, he is using the same driver. However that doesn't help us now, even if it would be a bug, and not a driver-issue, which I suppose.

---

### Post by Krytarik on 2010-12-17
> **kakila said:**
> (gnome-appearance-properties:7283): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7283): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed 

While working on a similar problem with Raugturi in another thread ([http://ubuntuforums.org/showthread.php?t=1633952](http://ubuntuforums.org/showthread.php?t=1633952)), this time with a ATI-card/chip, I discovered that I also get those error messages when running gnome-appearance-properties from terminal, although everything works fine at my machine at this aspect.

---

### Post by Krytarik on 2010-12-18
I read some other threads about similar issues in the meantime and I stumbled again over the "Module"-section in /etc/X11/xorg.conf, which I ruled out before, because the Readme of your driver says that the entries only have to be added when using older versions of xorg-xserver. And in xorg.conf also doesn't exist a Module-section, and it's working this way. As in fact I don't see some of them getting loaded in your log, just try adding them all to your xorg.conf.
```
Section "Module"
    Load "extmod"
    Load "dbe"
    Load "type1"
    Load "freetype"
    Load "glx"
EndSection

```Good luck!

---

### Post by kakila on 2010-12-18
Thanks for the help.

Recap: Problems after fresh install Ubuntu 10.10 keeping old /home (different partition)
1. Show my desktop button does not work
2. Windows have no decorations (cannot be moved, resized or closed)
3. Though NVidida drivers look fine, Normal level of visual effects cannot be applied.

- I tried reinstalling everything many times.
- I tried what have been suggested so far with no success (tried the modules section, nothing changes).
- I tried version 173, nothing changes, same problems.
- I tried a new user, this solves problems 1. and 2. and shows that there is something among the configuration files left in my ~ folder that mess up this part. However, the visual effects cannot be applied anyway.

The following action is to prune configurations one by one, that is to do
mv <configuration> <configuration>-old
and transform step by step my custom settings to a default one

I started with .gconf and .gconfd (I get rid of two errors in ~/.xsession-errors due to launchers of programs that are not installed by default in 10.10 (Amarok and Chrome)) but nothing else, problem remains.

I will update with my other attempts

---

### Post by Krytarik on 2010-12-18
After all I post my xorg.conf.
Though I see the xorg.conf-setup you have all the time in threads, you could check if the differences really make THE difference:
- commented the upper parts out, incl. the Xinerama-option
- I have specified a screen-resolution (the way I posted earlier, NVIDIA X Server Settings)
- the AddARGBGLXVisuals-option, which should also be on by default

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 15 05:52:31 PDT 2010

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010

#Section "ServerLayout"
#    Identifier     "Layout0"
#    Screen      0  "Screen0" 0 0
#    InputDevice    "Keyboard0" "CoreKeyboard"
#    InputDevice    "Mouse0" "CorePointer"
#    Option         "Xinerama" "0"
#EndSection

#Section "Files"
#EndSection

#Section "InputDevice"
#    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection

#Section "InputDevice"
#    # generated from default
#    Identifier     "Keyboard0"
#    Driver         "kbd"
#EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony CPD-4401"
    HorizSync       30.0 - 107.0
    VertRefresh     48.0 - 120.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 Ti 4200"
    Option         "NoLogo" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1152x864_85 +0+0; 1152x864 +0+0; 1152x864_100 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by kakila on 2010-12-18
Hi, partial SUCCESS

Problems 1. and 2. are solved. That is "Window manager error after fresh install Ubuntu 10.10 with old /home", showMyDesktop button not working and windows decorations missing.

SOLUTION: 
> mv ~/.local/share/applications ~/.local/share/old-applications

Log out and log in again, and everything should be ok.

Now the session works fine. The only problem remaining is the Visual effects. If this still doesn't work, you can try moving the complete ~/.local to ~/old-local.
If you have menus and panels looking ugly, do the same with ~/.gconf (NOTE: you will loose any launchers, background, wireless passwords and applets, etc you had, but you can just put them back)

---

### Post by kakila on 2010-12-18
Krytarik, I did what you suggested, still not working.

I have re-installed compiz (removed every package with compiz on its name, logout, login and install them again) and now the behavior is different (due probably to no clahses with old configuration files). I CAN activate the Normal visual effects but when they are active the decorations of the windows are gone!
I feel I am getting close.

Thanks a lot for the help. I will close this thread and start searching for the new problem in the forum.

---

### Post by Krytarik on 2010-12-18
> **kakila said:**
> I have re-installed compiz (removed every package with compiz on its name, logout, login and install them again) and now the behavior is different (due probably to no clahses with old configuration files).
That's weird though, because when you logged in with a fresh user there were no old home-files and it should have worked then also. Maybe some files of the compiz-packages were corrupted, but that would be unlikely after a fresh install. Anyway, good luck with the window decorations!

---

