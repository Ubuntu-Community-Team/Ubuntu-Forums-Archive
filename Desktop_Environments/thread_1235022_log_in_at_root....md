---
title: "log in at root..."
date: 2009-08-08
forum: Desktop Environments
---

### Post by AmerNewbieInDE on 2009-08-08
hello, i just installed ubuntu 904, i am trying to install a program, but it say it has to run under root. so, i log out, and try to log in as root, then i get error that sys admin cant log in from that screen, so, where and how do i run as root. i also tried to open root konsole i think it is, but it would not open.

---

### Post by lisati on 2009-08-08
The preferred method of running something which requires root privileges in Ubuntu is with the "sudo" command. Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by AmerNewbieInDE on 2009-08-08
ok, thanks, that works.. but problem now is... how do you kill xserver to install new nvidia drivers... i tried alt+ctrl+f1 and get a black screen, also sudo killall xserver only gives me error.. xserver: no process killed.. anyother ideas?

---

### Post by justsomedude on 2009-08-08
Go to System->Administration->Hardware Drivers and enable the restricted Nvidia driver.

---

### Post by sisco311 on 2009-08-08
> **AmerNewbieInDE said:**
> ok, thanks, that works.. but problem now is... how do you kill xserver to install new nvidia drivers... i tried alt+ctrl+f1 and get a black screen, also sudo killall xserver only gives me error.. xserver: no process killed.. anyother ideas?

```
sudo killall gdm
```

but, I would strongly suggest you to use the driver from the repos(go to System -> Administration -> Hardware Drivers to install it)

if you install the driver manually, then you will have to reinstall it after every kernel update.

---

### Post by AmerNewbieInDE on 2009-08-08
thanks justsomedude... forgot about that part..

[sisco311]("http://ubuntuforums.org/member.php?u=244665")... that only gives me a black screen, and have to reboot

---

### Post by mcduck on 2009-08-08
> **AmerNewbieInDE said:**
> ok, thanks, that works.. but problem now is... how do you kill xserver to install new nvidia drivers... i tried alt+ctrl+f1 and get a black screen, also sudo killall xserver only gives me error.. xserver: no process killed.. anyother ideas?

```
sudo /etc/init.d/gdm stop
```

..and to start it again:

```
sudo /etc/init.d/gdm start
```

Edit: Things will be a bit tricky if you're not able to use TTY's, without them and without GDM you'll have no way to use the system any more.

Perhaps you could try enabling framebuffer to see if that helps getting TTY's to work, some setups simply don't like the default resolution and setting up framebuffer with some resolution you know to work might help. To use framebuffer you'd add vga=XXX to your kernel options in /boot/grub/menu.lst, XXX being the code for the mode you want to use. (791 works for  most, it gives 1024x768 with 16-bit colors. You can also use "vga=ask" to get a selection of available modes at boot so you'll be able to try which one works)

---

### Post by AmerNewbieInDE on 2009-08-08
well, justsomedude.. thanks for the idea, but it didnt work, 

mcduck... i tried that, got a black screen but was able to get a blinking cursor, then got error that last process failed, something about resoluton. i have a widescreen notebook.. acer aspire 8730

---

### Post by justsomedude on 2009-08-08
> **AmerNewbieInDE said:**
> well, justsomedude.. thanks for the idea, but it didnt work, 


Could you be more specific about what exactly didn't work? If you get any error messages, please post them.

---

### Post by mcduck on 2009-08-08
Did you try enabling the framebuffer like I suggested? And if the "791"-mode didn't work did you try "vga=ask" to test the other possible modes?

---

### Post by AmerNewbieInDE on 2009-08-08
ok, let me see if i can get all this straight... oh btw, i am a newbie to linux so please forgive me... i am used to just clicking... lol

justsomedude.. no errors.. i deactivated the driver, tried to install, but it told me i have an xserver running, i restarted, tried again, but got the same thing..

mcduke... ok, so i didnt read your total post, i didnt see the part on framebuffer...is that done in terminal also?? i have a 19 inch monitor running 1680 * 945... the message said something about 1060, but didnt write it down...

---

### Post by AmerNewbieInDE on 2009-08-08
ok, first of all, please dont forget i am a newbie here...

justsomedude, i had no error till i ran the install.. then it told me i had xserver running, i disabled it in add/remove and also tried again after restart... but the i got the same message.

mcduke.. forgive me, i didnt see the part about framerate.. i am still tring to figure out what you meant by that...is that run in terminal?

---

### Post by AmerNewbieInDE on 2009-08-08
sorry,

---

### Post by justsomedude on 2009-08-08
> **AmerNewbieInDE said:**
> 
justsomedude.. no errors.. i deactivated the driver, tried to install, but it told me i have an xserver running, i restarted, tried again, but got the same thing..

When you say you deactivated the driver, does this mean you already had installed the restricted nvidia driver? 

Did it not work properly? Could you post a screenshot of the Hardware Drivers Window?

What happens when you issue
```
glxgears
```
from a terminal?


Also, please post the output of the following terminal commands so we can gather some information about your system:

```
lspci | grep VGA
```

```
lsmod | grep nvidia
```

and

```
cat /etc/X11/xorg.conf
```

Sorry for all the questions, I'm just trying to figure out your situation. You do realize installing drivers by hand is not common on Linux? Maybe you don't need to install the driver, you just dont realize that yet. ;)

---

### Post by mcduck on 2009-08-09
> **AmerNewbieInDE said:**
> 
mcduke... ok, so i didnt read your total post, i didnt see the part on framebuffer...is that done in terminal also?? i have a 19 inch monitor running 1680 * 945... the message said something about 1060, but didnt write it down...
It's not a terminal command but a piece of code you have to add to the configuration file to make TTY's run at higher resolutions (which is sometimes necessary since TFT displays are pretty bad at using anything else than their native resolution, and sometimes simply don't understand the default resolution used). You can edit the configuration file with any text editor you want.

---

### Post by AmerNewbieInDE on 2009-08-09
justsomedude, here is what you asked for, although i got nothing with lsmod | grep nvidia.

laptop:~$ glxgears
616 frames in 5.0 seconds = 123.061 FPS
624 frames in 5.0 seconds = 124.792 FPS
631 frames in 5.0 seconds = 126.055 FPS
629 frames in 5.0 seconds = 125.706 FPS
620 frames in 5.0 seconds = 123.837 FPS
632 frames in 5.0 seconds = 126.368 FPS
583 frames in 5.0 seconds = 115.810 FPS
44 frames in 5.1 seconds =  8.667 FPS
94 frames in 5.0 seconds = 18.663 FPS
102 frames in 5.0 seconds = 20.384 FPS
514 frames in 5.0 seconds = 102.771 FPS
628 frames in 5.0 seconds = 125.409 FPS
615 frames in 5.0 seconds = 122.868 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 18008 requests (14478 known processed) with 0 events remaining.

laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)

laptop:~$ lsmod | grep nvidia

laptop:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

---

### Post by AmerNewbieInDE on 2009-08-09
i tried to get a screenshot of my hardware drivers, but cant figure out how to get the image here.. the page says no proprietary drivers are in use on this system. it shows 2 nvidia accelerated graphics drivers, version 173 and 180. neither driver are activated. i have version 185 that i am trying to install.

---

### Post by AmerNewbieInDE on 2009-08-09
dont know how, but i finally got it installed..this is now with the nvidia 185 drivers...

laptop:~$ lsmod | grep nvidia
nvidia               9590404  39 
agpgart                42696  2 nvidia,intel_agp

laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)

laptop:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately 1/3 the monitor refresh rate.
14491 frames in 5.0 seconds = 2898.121 FPS
14594 frames in 5.0 seconds = 2918.613 FPS
14605 frames in 5.0 seconds = 2920.824 FPS
14597 frames in 5.0 seconds = 2919.390 FPS
14598 frames in 5.0 seconds = 2919.593 FPS
14607 frames in 5.0 seconds = 2921.373 FPS
14596 frames in 5.0 seconds = 2919.134 FPS
14445 frames in 5.0 seconds = 2888.750 FPS
5418 frames in 5.0 seconds = 1082.615 FPS
1875 frames in 5.0 seconds = 374.915 FPS
8876 frames in 5.0 seconds = 1775.176 FPS
14309 frames in 5.0 seconds = 2861.651 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 57 requests (57 known processed) with 0 events remaining.

the drop in frames is when i took the gears full screen

---

