---
title: "cannot get desktop effects to work so help needed"
date: 2007-12-10
forum: Desktop Effects &amp; Customization
---

### Post by ride1226 on 2007-12-10
here is the output of glxinfo

milby@milby-laptop:~$ fglrxinfo
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Warning, xpress200 detected.
Error: couldn't find RGB GLX visual!

milby@milby-laptop:~$ glxinfo
name of display: :0.0
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Warning, xpress200 detected.
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x26 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x29 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2b 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x30 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x31 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x32 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x56 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
milby@milby-laptop:~$ 

i can not get desktop effects to work for the life of me. PinkFloyd102489 has been helping me. My pc is a compaw presario v5000 with an ati xpress 200 graphics card which i have the drivers installed for. any help appreciated.

---

### Post by Ub1476 on 2007-12-10
Check this [guide]("http://www.ubuntu1501.com/2007/11/compiz-fusion-with-xgl-in-gutsy.html"). 

Also make sure your system is updated:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ride1226 on 2007-12-10
my output of fglrxinfo looks much different then how it does right there. here is mine.

milby@milby-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

milby@milby-laptop:~$ 


something is missing apparently and its on something called mesa project? which isnt ati like it says it should be.

---

### Post by ride1226 on 2007-12-10
my system is fully updated and upgraded. same output as above. and still can not get effects to work. maybe if i can get the output to go to ati like the above link gives an example of then it may work. i dont know. im really hitting a wall on this one.

---

### Post by erfahren on 2007-12-10
@ride1226

I take it that you have enabled the restricted driver. have you tried to install a newer version of the driver?  - I'm *not* suggesting that you do.

if there's another thread you were posting in can you give a link to that?

---

### Post by ride1226 on 2007-12-10
well this is where it all started

[http://ubuntuforums.org/showthread.php?t=635337](http://ubuntuforums.org/showthread.php?t=635337)

i thought beryl would be cool but didnt realize this new release has compiz-fusion in it and that does all the things beryl does. so i started working towards getting compiz to work.

then i posted in the last two pages of this thread and ended up doing a reinstall.

[http://ubuntuforums.org/showthread.php?t=385981&page=126&highlight=awn](http://ubuntuforums.org/showthread.php?t=385981&page=126&highlight=awn)

after the reinstall i got the restricted drivers installed with the help of pinkfloyd, got my flash working, and nothing else really. couldnt get desktop effects to work at all.

the graphics card in this computer is a ati xpress 200 if that helps at all. laptop is a compaq presario v5000.

---

### Post by erfahren on 2007-12-10
> **ride1226 said:**
> well this is where it all started

[http://ubuntuforums.org/showthread.php?t=635337](http://ubuntuforums.org/showthread.php?t=635337)

i thought beryl would be cool but didnt realize this new release has compiz-fusion in it and that does all the things beryl does. so i started working towards getting compiz to work.

then i posted in the last two pages of this thread and ended up doing a reinstall.

[http://ubuntuforums.org/showthread.php?t=385981&page=126&highlight=awn](http://ubuntuforums.org/showthread.php?t=385981&page=126&highlight=awn)

after the reinstall i got the restricted drivers installed with the help of pinkfloyd, got my flash working, and nothing else really. couldnt get desktop effects to work at all.

the graphics card in this computer is a ati xpress 200 if that helps at all. laptop is a compaq presario v5000.
ok, I just want to clarify my last post. -- i was just saying that I don't suggest you try to install a newer version of the ATI propritary driver (fglrx) - the one that is installed when you enable the Restricted Drivers should work.

Now, you said that you enabled it, but when you type in "fglrxinfo" it still says "Mesa"?. Can you go back to the Restricted Drivers Manager and make sure the driver is still checked off as being In Use?

---

### Post by ride1226 on 2007-12-10
Restricted driver manager says it is in use. fglrxinfo gives the following output...

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

milby@milby-laptop:~$

---

### Post by erfahren on 2007-12-10
can you post the output of
```

cat /etc/X11/xorg.conf

```

---

### Post by ride1226 on 2007-12-10
no problemo...here you go!

milby@milby-laptop:~$ cat /etc/X11/xorg.conf
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
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
        Driver          "fglrx"
        Busid           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection
milby@milby-laptop:~$

---

### Post by erfahren on 2007-12-10
from what it says the fglrx driver is being used. that's odd.

I would try reinstalling the fglrx driver - hopefully that would do its configuration automatically again and put it in use.

make sure you're updated and go into Synaptic Package Manager and search for "fglrx"
look for "linux-restricted-modules' and "xorg-driver-fglrx" mark both for reinstallation and apply. Then reboot. then see what the output of "fglrxinfo" is.

BTW: I guess I should mention that I'm somewhat of a novice Ubuntu user myself, but I've messed with this driver a lot!

---

### Post by ride1226 on 2007-12-10
well reinstalled both packages and rebooted....here is fglrxinfo output....

milby@milby-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

---

### Post by erfahren on 2007-12-10
ok, see post #53 in this thread: [http://ubuntuforums.org/showthread.php?t=588605&page=6](http://ubuntuforums.org/showthread.php?t=588605&page=6)

those guys were working on getting the newer version of the driver up and running but it's still relevant.

one question: do you have dual-monitors hooked up or anything?

---

### Post by ride1226 on 2007-12-10
ill check that post out. and no no dual monitors. im just on a compaq presario v5000 laptop.

---

### Post by ride1226 on 2007-12-10
i looked into  the xorg file like post 53 suggests to do and looked for warning...the first two warnings were just sayin only one monitor installed and something else irrelivent but then i found this

(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

that must be the problem right there. obviously compiz is 3d and i have no 3d acceleration available... so the DRI initialization failed. whatever that means.

any ideas?

---

### Post by erfahren on 2007-12-10
after taking a second look at your xorg.conf it seems that you're missing 

the Section "Files" is completely empty (it should contain the paths to fonts) and the Section "Modules" should have more in it (including Load "dri" and Load "glx").

Apparently the xserver isn't picking up and automatically configuring your hardware very well. You can try running:
```

sudo dpkg-reconfigure xserver-xorg

```
to reconfigre it manually. Much of the time you can accept the defaults. I was looking for a good HowTo or documentation to use it, but didn't come up with much except:
[http://www.mepis.org/docs/en/index.php/Dpkg-reconfigure_xserver-xorg](http://www.mepis.org/docs/en/index.php/Dpkg-reconfigure_xserver-xorg)
[http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server](http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server)

that utility will automatically make a backup of your xorg.conf but you can make your own ahead of time (name it whatever you want).
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup1

```

Just in the event that you cannot boot afterwards (slight possibility) I'll make another post on how to restore the backup.

---

### Post by erfahren on 2007-12-10
ok, if you need to restore the backup of xorg.conf

if xserver is unable to start you'll be taken into the recovery mode and prompted to enter the root password or continue trying to boot.

enter your password for the root. You should then be at the command prompt for root ( # ). 

change directory into /etc/X11
```

cd etc/X11

```
you can do a "ls" (list) to see the files, you should see your backup there. then to copy the backup over the messed up xorg.conf just:
```

cp xorg.conf_backup1 xorg.conf

```
(no need for sudo since you are logged in as root)

to reboot just do (shutdown reboot now)
```

shutdown -r now

```

---

### Post by ride1226 on 2007-12-10
i ran that, went to appearance, enabled effects, all the windows flickered and then came back after a second then it says "desktop effects could not be enabled"

---

### Post by erfahren on 2007-12-10
ok, hold on..
run fglrxinfo again and see if it says ATI and not Mesa
(I guess you probably rebooted after you did the reconfigure)

also, post the cat /etc/X11/xorg.conf again

---

### Post by ride1226 on 2007-12-10
i didnt reboot just restarted xserver by ctrl+alt+backspace

here is fglrxinfo

milby@milby-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.0.1

---

### Post by ride1226 on 2007-12-10
milby@milby-laptop:~$ cat /etc/X11/xorg.conf
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
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
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
        Identifier      "ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
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
        InputDevice     "Synaptics Touchpad"
EndSection

---

### Post by erfahren on 2007-12-10
apparently when you went through the reconfigure you didn't select "ati" for the driver (fglrx isn't showing up in the xorg.conf as the driver now).

(the opensource driver for ATI cards is called "ati", and fglrx is the proprietary driver that's enabled through the Resrticted Drivers. - then there's "vesa" which is the basic driver)

so going through the reconfigure didn't help. It still seems to be missing the Section "Module" and Section "Files".

I don't know, you might want to repost (again) and ask for help in getting it configured (and link to this thread). like "need help with dpkg-reconfigure xserver-xorg" or something.

--- just a note, when running fglrxinfo prints out ATI instead of Mesa you need to install the xserver-xgl package to get desktop effects.Hopefully you'll get to that point.

I apologize for not being able to help more.

---

### Post by ride1226 on 2007-12-10
actually i did select ati when i reconfigured which is pretty interesting. wonder why this just isnt working.

thank you for your help and no reason apologize. any help is better than no help.

---

### Post by ride1226 on 2007-12-11
milby@milby-laptop:~$ mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
milby@milby-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '1002:5955' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

milby@milby-laptop:~$ 


so my card is blacklisted so i followed wat the sticky said and here is my output

---

### Post by sweeper on 2007-12-11
I hope the OP doesnt mind my posting here, but I have had Compiz working with the non-restricted driver but it wont work with the restricted driver. 

FGRLX

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.0.6473 (8.37.6)


I reinstalled Compiz, cant think what else to try.

---

### Post by eperry2011 on 2007-12-13
Well, I'm a newbie with Linux as well (it won't be like that for long!), but I have the exact same laptop, and I'm having the exact same problem!  Actually, I've managed to get my fglrxinfo to output ATI:

```

ernest@ANONYMOUS:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

```

but I still cannot get the effects activated.  When I go to *System-->Preferences-->Appearance* and click over to the *Visual Effects* tab to try to change that to *Custom*, it tells me that *"The Composite Extension is not available"* I don't know what's going on with it.  Also, I upgraded from Ubuntu 7.04 to 7.10 - the mouse was working perfectly fine in 7.04, but when I upgraded, the mouse became really jumpy, sensitive, and sometimes doesn't cooperate.  I'm going to school for engineering, but I'm a freshman, so I don't know that much about the intricacies of Ubuntu and Linux in general as of yet........any help?!

---

### Post by eperry2011 on 2007-12-13
After searching further up here, I found this guide:

[http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+radeon+xpress+200m]("http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+radeon+xpress+200m")

I did what it said, and Compiz is working.....wobbly windows and all.  The mouse, however, is still glitchy (I'll look on another thread for that).  It was good to see that I wasn't the only one having this problem (people were wondering what was up with my laptop here at school!)

---

### Post by MachineBucket on 2007-12-13
> you need to install the xserver-xgl package to get desktop effects

I've been looking all over for a solution, that was it.

Thanks erfahren!

---

### Post by sune.ulf.hansen on 2008-01-16
I suspect that you will not be able to use compiz because the ATI Radeon 200 series only has 2d instruction set, and no 3d acceleration support.

I have just spent an hour trying to enable compiz in Gutsy Gibbon on what is supposedly a 9000 series Radeon. Nothing appear in "restricted drivers" so I just installed the ATI fglrx driver. That did not turn out well, so installed the driver from ATI. So far, nothing has worked for me.

As far as I remember this worked painlessly in Edgy Eft - I seem to recall building Beryl and running Google Earth back then.

Anyway, before you get too frustrated, look up whether compiz will run without 3d instruction support - if not then I do not think you will have much luck with a 200 series Radeon card - that might explain that "blacklisted" oddity.

---

