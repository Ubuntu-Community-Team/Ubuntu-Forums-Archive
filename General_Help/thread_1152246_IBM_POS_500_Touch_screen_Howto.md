---
title: "IBM POS 500 Touch screen Howto"
date: 2009-05-07
forum: General Help
---

### Post by pal.raistlin on 2009-05-07
I have been trying to get my POS screen working for the last few months Just found this hope it helps anyone else trying to do the same. I will copy paste google translation from 
[http://blog.pim-philips.ch/?cat=3]("http://blog.pim-philips.ch/?cat=3")


# the main issue I had was finding COM port 5

My Jukebox
4. October 2007, 14:51 clock by pim music, UNIX / Linux
In our company were old discarded computer models, such as a touchscreen Checkout IBM SurePOS 500 of Type 4840-531. Before this piece of history in the electronic storage was chartered, I could not help me, that cattle under the nail me to reality.

The idea is that this will be a touchscreen jukebox to make it with my stereo system to connect. The journey begins ...


Touchscreen fit?
Basic requirements that I've been asked this apparatus with Debian GNU / Linux Etch to operate. Debian was installed quickly, then I can not provide more. The touchscreen is on COM4 port and runs the Linux kernel by default only 4 COM ports, ie 0-3. Thus, the kernel reconfigured and newly baked; Linuxsourcen install and configure:

  # Cd / usr / src 
  # Apt-get install linux-source-`uname-r` 
  # Tar-xjvf linux-source-`uname-r`. Tar.bz2 
  # Ln-s linux-source-`uname-r` linux 
  # Cp / boot/config- `uname-r`. Config 
  # Make menuconfig 

By copying the current config File, the current kernel settings on the new kernel over. Then under Device Drivers/Character Devices/Serial Drivers the number of 8250/16550 serial ports from 4 to increase eg 8:




Now the kernel is baked and installed:

  # Make-kpkg-initrd binary 
  # Dpkg-i ../kernel-image- <xyz>. Deb 

Now the system must be restarted. Then you can use lsdev to verify that all interfaces were found.

IceWM and Touchscreen
X-Window installation and IceWM as window manager:

  $ Sudo apt-get install x-window-system icewm 

This model uses 3M Micro Touch, so this must still be installed:

  $ Sudo apt-get install xserver-xorg-input-micro touch 

To view the 3M Micro Touch touch screen driver must set the file /etc/X11/xorg.conf the following adjustments be made:

  Section "InputDevice" 
     Identifier "touchscreen0" 
     Driver "micro touch" 
     Option "Device" "/ dev/ttyS4" 
     Option "Minx" "1412" 
     Option "MaxX" "15184" 
     Option "Miny" "15372" 
     Option "Maxy" "1230" 
     Option "Screen Number" 0 " 
     Option "Reporting Mode" "Scaled" 
     Option "Button Number" 1 " 
     Option "SendCoreEvents" 
  EndSection 

The port lies with the SurePOS 500 to ttyS4 The values Minx, MaxX, Miny and Maxy be determined by a calibration that is not under X-window but takes place in the console. This must then touchcal be compiled, which can be found here: [http://touchcal.sourceforge.net](http://touchcal.sourceforge.net). 
This extract and then into the directory and compile:

  $ Cd ~ 
  $ Tar-xvvzf touchcal-<xyz> 
  $ Cd touchcal-<xyz> 
  $. / Configure 
  $ Make 
  $. / Touchcal m / dev/ttyS4 

The program now requires three calibration by touching the screen. The contact points are marked by a cross. Please allow time, as the initialization takes a little bit. The basic parameters in /etc/X11/xorg.conf will be sent to the XY values, the program after the calibration has ausgespuckt adjusted.

GDM and Autologin
Now, the touchscreen to work under IceWM running flawlessly. To be a touch screen solution is not to have to log in each time, the section [daemon] in the file /etc/gdm/gdm.conf adapted:

  [daemon] 
  AutomaticLoginEnable = true 
  Automatic Login = your user 

Once the login screen will appear again to fetch the password from then is calm.


Hope this helps

---

### Post by jpeddicord on 2009-05-11
Moved; please see [http://ubuntuforums.org/showthread.php?t=677396](http://ubuntuforums.org/showthread.php?t=677396) for tutorials & tips inclusion criteria, specifically the point that tutorials need to be original and not simply copied from another source. Thanks! :)

---

### Post by el_kolo on 2009-08-18
HI,

i have still problem with COM5. The main display is working on COM5 yes? I hae installed xserver-xorg-input-elographics drivers and configured xorg.conf like this:

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "InputDevice"
        Identifier  "ELO touchscreen"
        Driver "elographics"
        Option "Device" "/dev/ttyS4"
        Option "DeviceName" "ELO touchscreen"
        Option "MinX" "600"
        Option "MinY" "600"
        Option "MaxX" "3000"
        Option "MaxY" "3000"
        Option "ReportingMode" "Raw"
        Option "ScreenNumber" "O"
        Option "ButtonNumber" "1"
        Option "SendCoreEvents" "On"
EndSection

Section "ServerLayout"
        Identifier "Default Layout"
        Screen "Default Screen"
        #InputDevice "Generic Keyboard"
        InputDevice "ELO touchscreen" "SendCoreEvents"
EndSection

But it still doesn't work... Could you write something more how to activate ttyS4?

please help

---

### Post by el_kolo on 2009-08-18
to enable serial port 5 i had to add only 8025.nr_uarts=8 to kernel line in menu.lest.
But the cursor is not precise enough... any help?

---

