---
title: "No Desktop after Update"
date: 2011-01-25
forum: Desktop Environments
---

### Post by timmil on 2011-01-25
Well this morning I was notified that an update was available for a number of packages which I allowed to run.  After the update I rebooted my machine and now when I log in it plays my log in sound but I don't get my desktop and I have no idea where to start looking.  I am running 10.10.  I don't think it is a driver issue as I am able to get a desktop if I log in as a low graphics mode.  Any help on where to start or what I can do would be appreciated.

- Thanks!

UPDATE:

I was able to get into the system and ran the following command:

sudo apt-get -f install

and I received the following error message:

dpkg: parse error, in file '/var/lib/dpkg/status' near line 4790 package 'python-ubuntuone-client':
 field name `Prov' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by w3rt on 2011-01-25
try reinstalling your drivers through jockey-gtk

---

### Post by timmil on 2011-01-25
Ok,  I tried re-installing the current nvidia drivers and it was a no go still no desktop. Soo I backed out to ver 176 of the driver and it worked. So I decided to check ver 96 and it worked with it as well.  So it appears that something is broke with the current nvidia drivers.  So I have my desktop back but can't run the latest/current drivers for nvidia.

Thanks for your help!
- Tim

UPDATE:

I am not sure what to do.  I went in and enabled it back on the current version and it worked. However I noticed that the desktop visual effects were not working.  I tried to activate them, but am unable to.  Any thoughts??

---

### Post by Krytarik on 2011-01-25
Try to create a new "/etc/X11/xorg.conf", back it up before.

To save the configuration to the "xorg.conf":
- go to "System -> Administration -> NVIDIA X Server Settings"
- click at "X Server Display Configuration" on the left side
- check/choose your desired configuration
- click at "Save to X Configuration File"
- enter your "root"-password when asked
- choose replace, not merge!

---

### Post by timmil on 2011-01-26
> **Krytarik said:**
> Try to create a new "/etc/X11/xorg.conf", back it up before.

To save the configuration to the "xorg.conf":
- go to "System -> Administration -> NVIDIA X Server Settings"
- click at "X Server Display Configuration" on the left side
- check/choose your desired configuration
- click at "Save to X Configuration File"
- enter your "root"-password when asked
- choose replace, not merge!

I created a backup and a new xorg.conf file but I am still having the same problem.  I can use the current NVIDIA driver, but I am unable to turn on any desktop effects. Not sure why at this point.  Any other thoughts?

---

### Post by Krytarik on 2011-01-26
Try upgrading to the driver build by Ubuntu-X-Swat, they build them from the latest available versions of the proprietary drivers:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by timmil on 2011-01-27
Ok, I have a desktop and all is good. Most current drivers are loaded, however if I attempt to select the Extras, under the Visual Effects tab it will not apply the settings.  I ran the following command:

gnome-appearance-properties %F

which the gave me the following output:

There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.

(gnome-appearance-properties:10492): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory

(gnome-appearance-properties:10492): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start

Not sure what I am missing or why this is happening..

Any ideas?

---

### Post by Krytarik on 2011-01-27
I have to set the following option in the "Screen" section of my xorg.conf, although it is said to be enabled by default:
```
Option         "AddARGBGLXVisuals" "True"
```
Try that, if it doesn't work either, post your xorg.conf, also check "/var/log/Xorg.0.log" and "/var/log/messages" for error messages and post those as well.

---

### Post by timmil on 2011-01-27
> **Krytarik said:**
> I have to set the following option in the "Screen" section of my xorg.conf, although it is said to be enabled by default:
```
Option         "AddARGBGLXVisuals" "True"
```
Try that, if it doesn't work either, post your xorg.conf, also check "/var/log/Xorg.0.log" and "/var/log/messages" for error messages and post those as well.


I went ahead and did as you suggested and I am still unable to activate the "Extra"  Visual Effects  in the Appearance section.  It resets the screen and then takes me back to the screen with none selected.

Here is the xorg.conf file:

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.18  (buildd@muntries)  Sun Jan 23 21:51:54 UTC 2011

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
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 LE"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Thanks

---

### Post by Krytarik on 2011-01-27
Your xorg.conf seems to be ok so far.
- check if the specs of your monitor are set correctly
```
sudo apt-get install hwinfo
hwinfo --monitor
```- try to save the resolution through the mentioned "NVIDIA X Server Settings"
my mode options read like this:
```
Option         "metamodes" "1152x864_85 +0+0; 1152x864 +0+0; 1152x864_100 +0+0"
```If all that don't work, check "/var/log/Xorg.0.log" for errors.

Another way would be of course just to revert to version 176, or try to install the driver manually with the installer from Nvidia's website. But the would only be a last resort, because this way you would have to re-run the installer everytime the kernel gets updated, after ending up at the console login before.

EDIT: Since "/var/log/Xorg.0.log.old" is the log of the previous xserver session, you should also check those.

---

