---
title: "3 nvidia video cards, 9.04, x crash"
date: 2009-06-14
forum: General Help
---

### Post by headsmash on 2009-06-14
Fresh install my 0 monitor loads fine with the provided configs. However when I install the 180 provided proprietary drivers, upon reboot x crashes and I am prompted to reconfigure, use low graphics mode, load console. For now I have a single monitor plugged into each card.

Any thoughts on where I should begin? Goal is spanning monitor that can drag and drop across all monitors and probably compiz.
System is x64.

lspci
....
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1)
....

stock xorg.conf

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
----

---

### Post by headsmash on 2009-06-14
I have the same issue with the 173 drivers as well.

---

### Post by slamhound on 2009-06-14
I think I may have had the same problem.  X works after initial install, but then fails after install of nvidia drivers.  I had to run 

sudo nvidia-xconfig -a 

as described in this link:  [http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/](http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/)

Also, sometimes when you run that you get an error that it can't find libnvidia-cfg.so.1

If so, you need to create a symbolic link to the version-specific libnvidia-cfg.so.1 file (as described in this link:  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505863](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505863) ).  I think this happens if you use the Ubuntu nvidia drivers (but not if you use the ones downloaded directly from Nvidia.

But this may not be the same problem you had.  Good luck.

---

### Post by headsmash on 2009-06-15
> **slamhound said:**
> I think I may have had the same problem.  X works after initial install, but then fails after install of nvidia drivers.  I had to run 

sudo nvidia-xconfig -a 

as described in this link:  [http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/](http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/)

Also, sometimes when you run that you get an error that it can't find libnvidia-cfg.so.1

If so, you need to create a symbolic link to the version-specific libnvidia-cfg.so.1 file (as described in this link:  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505863](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505863) ).  I think this happens if you use the Ubuntu nvidia drivers (but not if you use the ones downloaded directly from Nvidia.

But this may not be the same problem you had.  Good luck.

Still booting into low graphics mode. I followed the instructions at the above links with adjustments made for x64. When issuing nvidia-xconfig, there were issues that referenced the kernel. I am reinstalling right now to have clean configs to work with.:popcorn:

---

### Post by nolliecrooked on 2009-06-15
install the latest 185.18.14 driver from here;

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

if that dosent work, just take out the 3rd 9500GT.

---

### Post by headsmash on 2009-06-15
> **nolliecrooked said:**
> install the latest 185.18.14 driver from here;

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

if that dosent work, just take out the 3rd 9500GT.


Take it out for the install? I need it for my other 3 monitors, 6 total.

Trying the install now, I believe that's what I dl'd last night however.

---

### Post by nolliecrooked on 2009-06-15
> **headsmash said:**
> Take it out for the install? I need it for my other 3 monitors, 6 total.

Trying the install now, I believe that's what I dl'd last night however.

woah, 6 monitors???

sorry man I know that. why do you need so many?

---

### Post by headsmash on 2009-06-15
> **nolliecrooked said:**
> woah, 6 monitors???

sorry man I know that. why do you need so many?


Well if 2 makes you 80% more efficient, then 6 should make me a googol times more efficient. Other than that, it lets me have around 9 consoles open and other things, I hate closing windows and tabbing.

I get the libGL.so.1 error "Warning: Unable to perform the runtime configuration check for library 'libGL.so.1' ('/usr/lib32/libGL.so.185.18.14'); assuming successful installation.

I appear to be working now, however I leave a mouse pointer on each screen which is odd, although not a big deal I guess.

---

### Post by nolliecrooked on 2009-06-15
> **headsmash said:**
> Well if 2 makes you 80% more efficient, then 6 should make me a googol times more efficient. Other than that, it lets me have around 9 consoles open and other things, I hate closing windows and tabbing.

I get the libGL.so.1 error "Warning: Unable to perform the runtime configuration check for library 'libGL.so.1' ('/usr/lib32/libGL.so.185.18.14'); assuming successful installation.

I appear to be working now, however I leave a mouse pointer on each screen which is odd, although not a big deal I guess.

lol okkkkkkkkkkkkk. well good luck (y)

---

### Post by jober on 2009-06-16
headsmash-
I am trying to what seems to be, the exact same thing.

I am trying to run 3 x 9500 on the same BusID's in fact.

I have been fighting with this for a couple weeks and the most I have been able to do, is to get 4 monitors working on 2 cards. It's a start, but I am used to 6 monitors, so it is pretty frustrating.

With 3 x 9500's, I can't even get X to start, so I can't do anything with my nvidia config, to configure monitors, etc. I am seeing NO ERRORS in my Xorg.0.log file and I have tried 50 different X configs, including writing my own from scratch several times. The Xorg.0.log appears to detect all 6 displays, X will just not start. 

I've tried the 2 bundled nvidia drivers, as well as a newer one (but still in the 180 release) to see if that would help, and all have the same result. No errors anywhere, but just won't start.

I also tried a GeForce 6400 PCI card, just to see if I could get that working. I can actually get X to load on 4 screens with that card in. The 3rd card is detected by the nvidia drivers and I can see the GPU in the config. When I try to enable any of the monitors on that card, X goes back to it's format of not starting.

I've emailed nvidia several times, but haven't heard a response.

I am running at 64bit system and I am nearing exhaustion of things to try... Any other thoughts or ideas at this point would be welcomed.

---

### Post by LowSky on 2009-06-16
install the driver by hand from consol, you will need to end your GDM sessions.

first download driver to the desktop
[http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/NVIDIA-Linux-x86-185.18.14-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/NVIDIA-Linux-x86-185.18.14-pkg1.run)

then switch to another consol, using Ctrl+ALT+F1

the kill your x session
```
sudo /etc/init.d/gdm stop
```

now change directory to desktop
```

cd Desktop
```

now run the linux driver

```
sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run
```
(If you hit TAB after the first N the rest of the filename will automatically appear. Remember, Linux is case sensitive so type a capital N) 
```

sudo reboot
```


more info see this post
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)


hope this works

---

### Post by jober on 2009-06-16
LowSky-
Still no go with the 185 driver. Same result as with 180.

Any other ideas?

---

### Post by jober on 2009-06-17
As a side note, I also have a GeForce 6200 that I tried in the configuration. I can at least get into X windows, with the other 4 screens active, with the 6200. I pull up the nVidia config (further than I ever get with the 3rd 9500) and I am able to see the other two (disabled) monitors.

If I enable them, X will not start. If I enable them and position all monitors in a single row (not how they are physically configured) and disabled Xinerama, all screens will turn on. However, without Xinerama enabled, even though each of the other screens has a start menu, etc, any programs started in that config go back to the base configured card. Also, it just doesn't work well if I have to have all 6 monitors configured in a row, versus stacked.

I am working off the assumption that paired monitors have to be stacked with their partner, since that is what I learned I had to do, to get 4 working in the first place.

If anyone has any suggestions, I am all ears.

Thanks-

---

### Post by jober on 2009-06-21
I have also tried a fresh install and every other version of the drivers that I could find.

Anyone else have any ideas how I could get the other 2 monitors to work, even if it were a different model/brand/whatever video card?

Thanks

---

### Post by headsmash on 2009-06-26
Was up and running for a few days, X would crash if I rebooted. If I did a cold boot I was fine, then I did the kernel update, now I'm back to a single monitor. I'm using the driver direct from Nvidia installed at cli.

---

### Post by headsmash on 2009-06-26
After an uninstall, reinstall and a few reboots i'm back up. This is going to get irritating every kernel update. To the others having issues. The downloaded drivers from nvidia work, make sure you get the x64 if you need them, most people seem to link the x86 drivers.

Compiz still doesn't work, but I wouldn't use it that much anyways...would just be nice.

---

### Post by Woody1987 on 2009-06-26
Are you sure your still using the driver with the new kernel? Try removing it and reinstalling it. Same thing happened to me with a kernel upgrade and the nvidia driver i installed myself from the command line.

---

### Post by Woody1987 on 2009-06-26
a program called DKMS is suppose to reinstall the module for any new kernels automatically. I dont know much about it so you may have to search the forums for an answer.

---

### Post by jober on 2009-06-27
Headsmash-

So are you up and running with 3 video cards, 6 monitors? If so, would you be willing to share your xorg.conf, so I can compare to mine, to try and figure out what is going on? I am still stuck at 2 GPUs and 4 screens. Pretty frustrating when I have 6 screens sitting here.

Thanks.

---

### Post by headsmash on 2009-06-29
> **jober said:**
> Headsmash-

So are you up and running with 3 video cards, 6 monitors? If so, would you be willing to share your xorg.conf, so I can compare to mine, to try and figure out what is going on? I am still stuck at 2 GPUs and 4 screens. Pretty frustrating when I have 6 screens sitting here.

Thanks.

This is with three hooked up until I resolve other issues. Just need to enable twinview for the other three I think. Until I figure out how to get this stable, I'm leaving my others on my other box.

cat /etc/X11/xorg.conf
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder62)  Wed May 27 01:59:40 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1680 0
    Screen      1  "Screen1" LeftOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
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
    ModelName      "Center"
    HorizSync       30.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Left"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Right"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    BusID          "PCI:2:0:0"
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    BusID          "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by headsmash on 2009-07-01
I stand corrected, post kernel updates and reinstall of x64 nvidia drivers from nvidia, I can not even reboot without losing my monitors and having to load low graphics mode. This and virtualbox/vmware doesn't appear to run.....damn.

---

### Post by jober on 2009-07-06
I was able to get 6 screens going by getting a Matrox TripleHead2Go and using 2 outputs from 1 video card (4 screens) and 2 from the second card (2 screens) to make the 6 screen arrangement.

Now my only issue is that my mouse pointer dissapears as it travels between screens at times.

Otherwise, I am finally up and running again on 6 screens.

---

