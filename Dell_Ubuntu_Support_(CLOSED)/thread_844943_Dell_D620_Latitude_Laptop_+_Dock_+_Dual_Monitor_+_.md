---
title: "Dell D620 Latitude Laptop + Dock + Dual Monitor + Compiz Effect Manual"
date: 2008-06-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vlonline on 2008-06-30
Hi Guys

In last several months I tried many times to set up my Dell D620 laptop to work properly in dock station with dual monitors. And I failed, ended up with 'vsae' generic video driver + single external monitor. Working with generic driver means zero chance to see any compiz effect. But I have many work to do on my machine, so as long as it can work, just leave it.

But this morning, I got some time to get my hands on it again. So I start from step 0 to 10 (I think less than 10) manage setting my Dell D620 work properly in dock and display in dual external monitor with compiz effect enabled. Here I share my experiment notes.

For your reference, I list my hardware setting blow

Here list my laptop hardware info 

(Attention: my Dell D620 is using Nvidia Quadro NVS 110M)

```
$lspci | more

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

My start up environment is that a Ubuntu 8.04 was installed in my dell D620 with docking and a Dell 1907fv LCD monitor connect to dock DVI output. 

In my experience, you only need to dock your D620 laptop and install Ubuntu 8.04 straight forward, then will end up with the same environment with mine.

Because I messed up the x configuration file in the last several months, so I decide to start from a clean one.

**Step 0:** Back up your current setting
```
sudo cp /etx/X11/xorg.conf /etc/X11/xorg.conf.my.backup
```

**Step 1:** Reconfigure your Xserver.
```
sudo dpkg-reconfigure xserver-xorg
```

**Step 2:** Uninstall any installed nvidia glx drivers and setting utility.
Because my system was installed nvidia-glx-new several months before. So I run the following command
```
sudo aptitude remove nvidia-glx-new
```
```
sudo aptitude remove nvidia-settings
```

**Step 3:** Connect my second Dell 1907fv monitor to dock analog output, then Restart system

Up here, you should end up in a clean installation environment. When it start up again, my second monitor was in standby mode (This is normal to me, I used to that for months). Now let's light it up.

**Step 4:** Install Nvidia glx driver. Because I simply want to use my second monitor, not caring about 3D effects, so I start with nvidia-glx driver. So I ran the following command
```
sudo aptitude install nvidia-glx
```
```
sudo aptitude install nvidia-settings
```
```
sudo nvidia-xconfigs
```
```
sudo shutdown -r now
```

It was very interesting, after restart, my second monitor (connect to analog connector) works instead of the DVI connected one. Anyway, as long as I can see the desktop, then I am not hopeless.

Step 5: Start your nvidia-settings
```
sudo nvidia-settings
```

In the setting window, select the "X Server Display Configuration", you should see three square boxes stands for connected monitors in the layout window. Then click the "Disabled" monitor (not the 'LPL' one)  and select the "configure..." button and select TwinView radio button. Then OK. Then Apply. You should see the change now. In my case, two external monitors rock now. 

But one problem happen, windows can not be dragged between monitors. So I **save the current setting** and **make a backup**, then go into configure selections again, select "separate X Screen" and OK (prompt restart system required) then click Xinerama selection. Save this setting to configuration file (deselect merge configuration)  and restart.

After restart, you should able to drag windows between monitors.

------------------------------- Extra ------------------------------------
Now, I m a bit aggressive, I want to enable the compiz effect. So I start over again

**Step X.0** Backup current xconfig. 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.dm-separate
```

**Step X.1** Uninstall nvidia drivers
```
sudo aptitude remove nvidia-glx
```
```
sudo aptitude remove nvidia-settings (I just make it clean to start, so uninstall it anyway)
```
```
sudo aptitude install nvidia-glx-new
```
```
sudo aptitude install nvidia-settings
```
```
sudo nvidia-xconfig
```
```
sudo shutdown -r now
```

After restart, I still can see the separate screen configuration in use. **Backup this configuration file again.**

**Step X.2** Change to TwinView
Because compiz can not work under separate screen mode. So we need to change to use TwinView. Start your nvidia setting window.
```
sudo nvidia-settings
```

Select the "X Server Display Configuration", then select any external monitor box in the layout window, press configure button and select TwinView option and OK (Prompt restart required). Then apply the settings. Save the configuration file (de-select merge) and restart system.

After restart, the TwinView works. And it is interesting, this time, I can drag windows between monitors (Don't know why, who knows that please tell me. I m still a newbie). Backup the configuration file again. The start "apparent setting" and enable the effect. 

**Step X.3 **Install the Compiz setting manager.
```
sudo aptitude install compizconfig-settings-manager
```

Now you can customize all the effects. 


If you fail in any steps stated above, load back your backup configuration file and check x11 log in /var/log/Xorg.0.log

Enjoy your dual monitors.

At last, my X configuration file end up as following 

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Tue Mar  4 20:24:34 UTC 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    ModelName      "DELL 1907FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 110M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

```
$glxinfo | grep version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.3
OpenGL version string: 2.1.2 NVIDIA 169.12

```

```
$uname -srvom
Linux 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
```

---

### Post by ballin on 2008-06-30
That's good timing, I'm setting up the EXACT same setup tonight!
Will let you know how I get on!

I already have it running compiz + dock + single monitor

---

### Post by Lunar_Lamp on 2008-08-28
Could you give me the config for your setup ballin? That's the exact setup I want!

---

### Post by Lunar_Lamp on 2008-08-28
I got it working, so just in case anyone else has similar problems, here is my config (single monitor connected to the dock, and compiz enabled).

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
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
    ModelName      "DELL 1908FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 110M"
EndSection

Section "Screen"

#    Option         "TwinView" "1"
#    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1280+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Wolfhere on 2008-09-10
Thanks Lunar. Almost exactly as I am doing, same laptop, different LCD though (Viewsonic 1932WM). In the past, everytime I try booting to Ubuntu (dual boot - Windows vista on the other drive), I get the black screen when docked. I found another post by someone in this forum that talks about going to TTY before docking, docking, going to the X screen (Ctrl-Alt-F7) and restarting X. 
:confused:Did you have to do this?
:confused:Did you add a second monitor in the nvidia-settings? or
Did you manually edit the xorg.conf? :eek:

PS. Glad you posted your xorg.conf.

---

