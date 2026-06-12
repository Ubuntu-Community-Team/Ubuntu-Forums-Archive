---
title: "Problem with the installation of nvidia drivers"
date: 2011-02-26
forum: Desktop Environments
---

### Post by kospanak on 2011-02-26
Hello. I tried to install the latest nvidia drivers for 8.04LTS Ubuntu linux
and i can't change the resolution(all i can choose is 800x600 or 640x480). When i tried to set the Nvidia X Server settings, it showed that i don't use the driver therefore i had to edit the X configuration file (nvidia-xconfig). I did that but alla i get is this

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.

What could be the roblem

---

### Post by thefasterblueone on 2011-02-26
Maybe this will help.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")


To be able to write to xorg.conf, nvidia-xconfig must be run as root.
Code:

```
sudo nvidia-xconfig
```


Let us know if you still need some help.

---

### Post by kospanak on 2011-02-26
I did and i got this

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

But still when i type sudo nvidia-settings i still get this message:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by realzippy on 2011-02-26
Means 270,xx driver ?
Which X server version/kernel do you run?
Which driver did you use before?
If none or fresh install why not installing supported version?
Which graphics card?

---

### Post by Krytarik on 2011-02-26
> **kospanak said:**
> I did and i got this

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

But still when i type sudo nvidia-settings i still get this message:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
Did you reboot/relogin after doing this!?

---

### Post by kospanak on 2011-02-27
The card i use is Geforce 6600GT. I did reboot the machine and every time, before logging in ubuntu, a message appears, that i am running linux in low graphics and i must configure the screen and the graphics card along with the drivers. I did the configuration (because the company, which provided the screen, doesn't appear i choose generic). And yet the tests are always failing and i still have low resolution and no ability to use the drivers.

---

### Post by Krytarik on 2011-02-27
Use the following command to create a new, fresh xorg.conf, maybe that helps:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```

---

### Post by kospanak on 2011-02-27
I tried it but still i get this message when i got to nvidia settings

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by Krytarik on 2011-02-27
Then I suppose the driver is not properly installed, or isn't appropriate for the version of Ubuntu you are running. How did you install it?

Like *realzippy* asked, why don't you use a current Ubuntu version?
Did you run an earlier version of the driver successfully before?

---

### Post by kospanak on 2011-02-27
i tried to install the latest driver when i had the 8.04 Ubuntu linux. I used the add/remove programs. Now i have my linux ugraded to 10.04 version. I tried to install nvidia-glx but i still had problem

---

### Post by Krytarik on 2011-02-27
> **kospanak said:**
> i tried to install the latest driver when i had the 8.04 Ubuntu linux. I used the add/remove programs. Now i have my linux ugraded to 10.04 version. I tried to install nvidia-glx but i still had problem
Please do the following:
- remove the driver packages you installed manually, check "/var/log/apt/history.log" for that
- install the "recommended" proprietary driver via "System -> Administration -> Hardware Drivers"
- run the previously given command
- reboot/relogin

---

### Post by kospanak on 2011-02-27
i still have a question. Could there be anything wrong with the xconf file?

---

### Post by Krytarik on 2011-02-27
> **kospanak said:**
> i still have a question. Could there be anything wrong with the xconf file?
Usually the xorg.conf is set up properly when running the given command, unless you need/want something special.

---

### Post by kospanak on 2011-02-28
I did what you said but i have a new problem

 every time i switch on the computer i get this message

(EE) NVIDIA(GPU-0): Your GeForce 6600 GT graphics card does not have the necessary
(EE) NVIDIA(GPU-0):     external power cables attached; X will not start unless
(EE) NVIDIA(GPU-0):     this is rectified.  Please shut down your computer, open
(EE) NVIDIA(GPU-0):     its case, and attach the appropriate power connectors. 
(EE) NVIDIA(GPU-0):     Your video card may have multiple power connectors.  If
(EE) NVIDIA(GPU-0):     so, each must be attached to a separate power cable. 
(EE) NVIDIA(GPU-0):     Please see the documentation provided with your video card
(EE) NVIDIA(GPU-0):     for more details.  If you think you have received this
(EE) NVIDIA(GPU-0):     message in error, you may specify the
(EE) NVIDIA(GPU-0):     "NoPowerConnectorCheck" X configuration option in the
(EE) NVIDIA(GPU-0):     Screen section of your X config file.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.


And as usual the nvidia-settings give me the same message:

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by Krytarik on 2011-02-28
Like I asked before, did you EVER run your card with any version of the proprietary driver successfully before? Or do you also have Windows, and if so, does it work there?

---

### Post by kospanak on 2011-02-28
yes i have and i didn't have a problem. in windows i had a warning that there wasnt enough power to have the fully utilized capabilities of the card. Still i deactivated the warning and i didnt have any problem

---

### Post by Krytarik on 2011-02-28
> **kospanak said:**
> yes i have and i didn't have a problem. in windows i had a warning that there wasnt enough power to have the fully utilized capabilities of the card. Still i deactivated the warning and i didnt have any problem
Are you able to attach those power cable then!?

You could also choose to do this:
> 
(EE) NVIDIA(GPU-0): message in error, you may specify the
(EE) NVIDIA(GPU-0): "NoPowerConnectorCheck" X configuration option in the
(EE) NVIDIA(GPU-0): Screen section of your X config file.


---

### Post by kospanak on 2011-02-28
I added the NoPowerConnectorCheck but i still have the same problem.

---

### Post by Krytarik on 2011-02-28
Please post your current xorg.conf then, in code-tags please (the #-button in the editor).

---

### Post by kospanak on 2011-02-28
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 22 11:44:23 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoPowerConnectorCheck" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by Krytarik on 2011-02-28
Some put it into the "Device" section instead, try it there. Also try without "True", means nothing after it, and also with "1".

---

### Post by kospanak on 2011-02-28
I did what you said and it worked. Thanks mate. But i wonder what the difference is...

---

### Post by Krytarik on 2011-02-28
> **kospanak said:**
> I did what you said and it worked. Thanks mate. But i wonder what the difference is...
Actually, I wonder why it is advised to put it into the "Screen" section, since the check of the power cable actually regards the video card, thus "Device", and not the output of it.

---

### Post by kospanak on 2011-03-01
I sought advice from similar threads and someone put that option in the Screen section. Still, once again, thanks mate

---

### Post by Krytarik on 2011-03-01
As it is also advised in the driver output:
> 
(EE) NVIDIA(GPU-0): message in error, you may specify the
(EE) NVIDIA(GPU-0): "NoPowerConnectorCheck" X configuration option in the
(EE) NVIDIA(GPU-0): Screen section of your X config file.

And I did also see threads where it has been put into those. ;-)

---

