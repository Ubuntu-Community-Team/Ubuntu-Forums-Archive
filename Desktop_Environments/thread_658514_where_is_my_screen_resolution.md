---
title: "where is my screen resolution?"
date: 2008-01-04
forum: Desktop Environments
---

### Post by delilahjed44 on 2008-01-04
I have tried to change my resolutions 4 times now, and it wont change, needing 1024 by 768? why wont it work> ? Using Ubuntu 710? it will not change even when I except the change what is up here? never had this issue before?

 sherri

---

### Post by PinkFloyd102489 on 2008-01-04
```
dpkg-configure xorg-server
```



Try that in terminal. When screen resolutions come up, select the ones you want with Spacebar.

---

### Post by taurus on 2008-01-04
What graphic card do you have?  Open a terminal, Applications -> Accessories -> Terminal, and run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, restart your X again with <Ctrl><Alt>Backspace.

---

### Post by delilahjed44 on 2008-01-25
> **taurus said:**
> What graphic card do you have?  Open a terminal, Applications -> Accessories -> Terminal, and run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, restart your X again with <Ctrl><Alt>Backspace.

Hello, I am not sure the exact card,...it is NVIDIA, now what happens is, I leave my Ubuntu on...sometimes I come back in and the screen is all jig-jagged around, so I restart, this has happened about 3 to 4 times in the last two months.  When I restart I cannot get the  resoluions to enlarge, I need 1024 by 768 or it is not ledgible for me to read.  Ok then it wont resize no matter what I do,  I try to change resolution but now its not even asking me if I want to keep these settings...when it did ask me this before the settings never changed even when I tried to save them.  I did what was requested of me above, I dont understand about restarting X again, I have Ubuntu 710 Gutsy Gibbon.  However I restarted the machine and I am receiving the same problem.   I originally thought it may have something to do with the processor since its possible I downloaded the AMD version of ubuntu and this is the 1386 one, not sure on that,,,heard it should work anyway...I certainly dont want to go back and try to battle adobe to work again, took me two weeks before to get that all running.  What can I do here to fix the resoluion issue?

Thank you
Sherri

---

### Post by delilahjed44 on 2008-01-25
> **taurus said:**
> What graphic card do you have?  Open a terminal, Applications -> Accessories -> Terminal, and run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, restart your X again with <Ctrl><Alt>Backspace.

 Hello, I did this twice but do not understand what you are askin me to do as far as the x thing? here is what I receive but please not the numbers are different on both occasions towards the bottom? 

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080125172449<< different from below?

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080125174508 << different from above?

 I have not up-dated anything but I am not using any compiz fusion desktop but even so dont see anything usful for a steady resolution anyway?

Thank you 
sherri

---

### Post by taurus on 2008-01-25
> **delilahjed44 said:**
> Hello, I did this twice but do not understand what you are askin me to do as far as the x thing? here is what I receive but please not the numbers are different on both occasions towards the bottom? 

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; **[COLOR="Blue"]backup in /etc/X11/xorg.conf.20080125172449<< different from below?[/COLOR]**

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; **[COLOR="Blue"]backup in /etc/X11/xorg.conf.20080125174508 << different from above?[/COLOR]**

 I have not up-dated anything but I am not using any compiz fusion desktop but even so dont see anything usful for a steady resolution anyway?

Thank you 
sherri

When you reconfigure your X with that command, it will make a backup copy of your original /etc/X11/xorg.conf.  The first four digits are for the year, 2008.  The next two are the month, 01.  The next two are for the day, 25.  and the last six digits are for the hours, minutes, and seconds.  So if you run that command the second time, the last six digit will be different, increasing.

Let's see exactly which nvidia graphic card do you have?  Post the output of this command here.

```
lspci
```
Also, look in /etc/X11/xorg.conf to see which **Driver** do you currently use.

```
cat /etc/X11/xorg.conf
```

---

### Post by delilahjed44 on 2008-02-03
Thank you on this...the above did work, I have made it a habit just to shut the machine down at night and start back up, in this it doestn do the jig/jag screen thing and it opens up to the proper resolution each time...Thank you so much of input, it is really appreciated,  I dont have much time with trying to correct my issues on my computer so its easy for me to get lost along the way understanding exactly what to do, thank you all for your patience, I know I am not easy to deal with...thank you again very much.

Sherri

---

### Post by delilahjed44 on 2008-02-23
> **taurus said:**
> When you reconfigure your X with that command, it will make a backup copy of your original /etc/X11/xorg.conf.  The first four digits are for the year, 2008.  The next two are the month, 01.  The next two are for the day, 25.  and the last six digits are for the hours, minutes, and seconds.  So if you run that command the second time, the last six digit will be different, increasing.

Let's see exactly which nvidia graphic card do you have?  Post the output of this command here.

```
lspci
```
Also, look in /etc/X11/xorg.conf to see which **Driver** do you currently use.

```
cat /etc/X11/xorg.conf
```

 Hey thanks alot on this,,, I always come back and re-check my notes, so far so good, here is the info in the terminal from your request..

 lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
02:0b.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
02:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
 

 /etc/X11/xorg.conf
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

 EEKKK!!! was you expecting all of this,,,I sure dont know what to look for...ok just dropping this off, 

Thanks everyone for always putting up with me, GRACIOUS...my lil Ubuntu keeps me jumping!

---

