---
title: "HOWTO: Desktop Effects + Gutsy + ATI x1400"
date: 2007-10-12
forum: Desktop Effects &amp; Customization
---

### Post by bwhite82 on 2007-10-12
****HOWTO outdated Please use the following links to the Wiki to get desktop effects working with your video card:****

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

[https://help.ubuntu.com/community/DesktopEffects?highlight=%28effects%29%7C%28desktop%29](https://help.ubuntu.com/community/DesktopEffects?highlight=%28effects%29%7C%28desktop%29)




I had some trouble getting Gutsy's new Desktop Effects working when I upgraded, so I thought I'd post the steps I took so that it may help others.

**1)** Make sure you have the tools you need to compile the driver:

> sudo apt-get install module-assistant build-essential debhelper debconf dh-make fakeroot libstdc++5 linux-headers-generic

**2)** Go here: [http://ati.amd.com/support/driver.html]("http://ati.amd.com/support/driver.html") and download the latest Linux driver. As of this posting, 8.40.4 is the latest.

**3)** CD to the directory where you downloaded the file and type:

> sudo bash ati-driver-installer-[driver version].x86.x86_64.run --buildpkg Ubuntu/gutsy
This will create a few .deb packages which you will install in step 5.

**4)** Blacklist fglrx:

> sudo gedit /etc/default/linux-restricted-modules-common

Scroll down to "DISABLED_MODULES" and put fglrx into the quotes.

**5)** Install driver:

> sudo dpkg -i xorg-driver-fglrx-[driver version].deb fglrx-kernel-source-[kernel version].deb

**6)** Compile and install the kernel module:

> sudo module-assistant prepare,update
sudo module-assistant build,install fglrx
sudo depmod -a
[B]
7)[/B] Install XGL (Needed for ATI users at this time for desktop effects:

> sudo apt-get install xserver-xgl

Now either hit CTRL+ALT+BKSP to restart X or simply reboot your computer.

**Hope this helped someone! If you run into any problems, please post a new thread or post here, but do know that I cannot provide support for this HOWTO, I simply lack the knowledge.**

---

### Post by jctweb on 2007-10-13
> **Soldierboy said:**
> **7)** Now click System>Preferences>Desktop Effects and Enable them.[/B]

I don't have that menu in Kubuntu - are you aware of something similar for us KDE users?

Thanks

---

### Post by Forlong on 2007-10-14
> **jctweb said:**
> I don't have that menu in Kubuntu - are you aware of something similar for us KDE users?
No, in fact not even GNOME has this on Gutsy.
I guess what Soldierboy meant was *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects*

But that's GNOME only. On KDE you have to run *compiz* via [Alt]+[F2]
Or create a starer on the desktop (or panel) with *compiz* as command.

---

### Post by Ub1476 on 2007-10-14
Why not just enable through the Restricted Driver Manager? I do.

---

### Post by bwhite82 on 2007-10-14
> **Forlong said:**
> No, in fact not even GNOME has this on Gutsy.
I guess what Soldierboy meant was *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects*

But that's GNOME only. On KDE you have to run *compiz* via [Alt]+[F2]
Or create a starer on the desktop (or panel) with *compiz* as command.

No, I just double-checked myself, it is: Preferences>Desktop Effects

Although, the menu option that you listed is available as well.

A screenshot is attached showing my Ubuntu version and menu option.

---

### Post by superduckwc on 2007-10-14
Hi!
When I want to install driver, when I type:
 sudo bash ati-driver-installer-8.40.4-x86.x86_64.run --buildpkg Ubuntu/gutsy

It marks:

Generating package: Ubuntu/gutsy
./packages/Ubuntu/ati-packager.sh: line 58: dpkg-architecture: command not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.S12771

Do you know why?

---

### Post by tidiazuron on 2007-10-15
@superduckwc
I had the same problem. You need to have dpkg-dev installed in your system. Look for it in Synaptic or type:

 sudo apt-get install dpkg-dev

in a terminal.

Edited:
That would answer your question, but you will need debhelper and module-assistant as well to build the package.
 sudo apt-get install debhelper module-assistant

Hope this will help.

---

### Post by Forlong on 2007-10-15
> **Soldierboy said:**
> No, I just double-checked myself, it is: Preferences>Desktop Effects
Then it's still there from your Feisty install. Gutsy does not have the desktop-effects package and therefore this button/GUI anymore.

Sorry, I didn't know the upgrade does not remove this package - it should, since it's not designed to work with Gutsy. I recommend removing it.

---

### Post by bwhite82 on 2007-10-15
> **Forlong said:**
> Then it's still there from your Feisty install. Gutsy does not have the desktop-effects package and therefore this button/GUI anymore.

Sorry, I didn't know the upgrade does not remove this package - it should, since it's not designed to work with Gutsy. I recommend removing it.

Ah, it seems that you are quite right. I did a partial upgrade to Gutsy and the menu option was still there.

On another note, forgot to mention that some compiling tools are needed to compile the driver/kernel module, I have added another step above.

---

### Post by superduckwc on 2007-10-15
@ tidiazuron

Thanks! It works now...only installation, but effects are stil unavalaible. XGL session is stopped when gnome launch, Anyway, I'm going to wait the new driver from ATI:guitar:

---

### Post by mfergus3 on 2007-10-18
Hey guys,

Newbie here, running 7.10 on a dell laptop with an ATI X1400.   When I try to run the installer, I get an error: "make: dh_testdir: Command not found".  

I assume that's because I don't have all the packages installed, but I when I try to install half of them, I get "Couldn't find package {package}" responses.  I'm sure this is a dumb question, but help would be appreciated :)

---

### Post by DrQuincy on 2007-10-18
How come you have to put fglrx in disabled modules?

---

### Post by cversion7 on 2007-10-18
I've been working on this for hours, trying every single "how to" I can find and I give up for now. 

Thinkpad T60, Radeon Mobility X1400

After the last "how to", I get finished and X (or something) crashes when I run fglrxinfo in terminal and I end up at the login screen. I get artifacting graphics on text and scrolling through text takes a long time to refresh (as though I have the wrong driver or something). Now I get to figure out how to remove all the crap I've done, which hopefully I can do without having to reload it (yet again).

I was hoping to get 3d working so I could possibly play games on it (since I do just fine under Windows), but I guess that'll have to wait.

Signed,

Frustrated with Linux but still trying to love it...

---

### Post by DrQuincy on 2007-10-19
> **cversion7 said:**
> Frustrated with Linux but still trying to love it...

I completely agree with you.  I'm disappointed they made out it would have all this out of the box support but it's all bullsh*t.  I'm close to ditching Linux now.  Well, Ubuntu at least.  Nothing ever seems to get finished or tested properly.

---

### Post by Forlong on 2007-10-19
> **DrQuincy said:**
> I'm disappointed they made out it would have all this out of the box support but it's all bullsh*t.
Who made such statement?
> **DrQuincy said:**
> I'm close to ditching Linux now.  Well, Ubuntu at least.
Because such elementary things you possibly could never live without, as desktop effects?
> **DrQuincy said:**
> Nothing ever seems to get finished or tested properly.
You do know the only people you have to blame here are the ones working for ATI?
Don't blame Linux if it doesn't get proper support by hardware vendors.

I know it's frustrating. I have an ATI myself but I know whose damn fault it is, I can't use Linux' full potential.


Sorry for the rant but please keep in mind that many things just can't be "finished" by Linux/Ubuntu alone.

But to answer your previous question (finally): this How-To makes use of the latests driver provided directly by ATI (and therefore not tested by Ubuntu). I don't know if it's really necessary, though.

---

### Post by Jfire03 on 2007-10-19
I'm using linux for the first time. Installing Ubuntu 7.10. I'm having problems enabling the desktop effects. I tried every step in this how-to and didn't have any trouble. But I try enabling the desktop effects and get a message saying the effects couldn't be enabled. That's all it says.

I have an ati mobility radeon x1300 in a dell inspiron.

If anyone knows what the problem could be, please help.

---

### Post by Forlong on 2007-10-19
Please post the output of ```
compiz
``` in a terminal and use the forum's CODE tag please (# button)

---

### Post by Jfire03 on 2007-10-19
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

---

### Post by Forlong on 2007-10-19
> **Jfire03 said:**
> Checking for Xgl: present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
Seems like there are troubles with the fglrx driver. What output gives:
```
fglrxinfo
```

---

### Post by Jfire03 on 2007-10-19
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.0.6747 (8.40.4)

---

### Post by JBAlaska on 2007-10-19
When I upgraded to the rc, I just had to remove ccsm (conflicting with desktop effects version ?) and reinstall emerald, then CF was back up and more stable than it's ever been (for me). See my sig for my computer specs.

It's nice to not have to start xgl with a script and also that CF autostarts emerald.

---

### Post by Amaranth on 2007-10-19
Here is a more 'correct' howto:

1. Go to *System &#8594; Administration &#8594; Restricted Drivers Manager* and enable the ATI driver.
2. Install the xserver-xgl package.
3. Restart your computer and the effects should automatically come on. If not, go to *System &#8594; Preferences &#8594; Appearance, Visual Effects tab* and turn them on.

---

### Post by nerkman on 2007-10-19
Arrrggghhh....

WTF is going on with xgl?  I've tried following the instructions on this thread and it can't find either xgl, the deb assistant, etc. to compile the ati driver.  No matter which ati driver I try in System -> Administration --> Screen And Graphics, it doesn't work or I get a distorted gray screen.

I have a Radeon 9250 128MB, BTW.

If I try and go in "Restricted Drivers" a pop-up says I don't need any.  That's it.

Before you ask, I have the 7.10 disc in the CD drive and I am connected to the internet.  What gives with all this?  This is a fairly significant bug, AFA I'm concerned, and most of this isn't ATI's doing.

---

### Post by Amaranth on 2007-10-19
You don't need this driver (it won't even work) and you don't need Xgl.

---

### Post by Forlong on 2007-10-19
> **nerkman said:**
> If I try and go in "Restricted Drivers" a pop-up says I don't need any.
That means ATI doesn't support your graphics card anymore.
You have to use the open radeon driver. Compiz should work with AIGLX then (no need for Xgl).

---

### Post by nerkman on 2007-10-19
Ok, so how do I enable AIGLX?  Because right now, I can't enable desktop effects.

Aside from that, I would like to note, Gutsy rocks.  Odd that I didn't have this problem with RC1 live CD.

---

### Post by nerkman on 2007-10-19
BTW thanks for all your help so far.

---

### Post by Forlong on 2007-10-19
> **nerkman said:**
> Ok, so how do I enable AIGLX?  Because right now, I can't enable desktop effects.
You can post your xorg.conf and we will see, if there's anything wrong.
A> **nerkman said:**
> Odd that I didn't have this problem with RC1 live CD.
Then maybe your graphics card has been blacklisted by now.
Try running Compiz like this:
```
SKIP_CHECKS=yes compiz
```

---

### Post by nerkman on 2007-10-19
Ok, here goes...  BTW, thanks for your help:

```
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
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
    Option        "XkbVariant"    "alt-intl"
    Option        "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
    Boardname    "ATI Radeon (vesa)"
    Busid        "PCI:1:0:0"
    Driver        "vesa"
    Screen    0
    Vendorname    "ATI"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Vendorname    "Hewlett-Packard"
    Modelname    "HP A4033A 21-inch Display"
    Horizsync    30-80
    Vertrefresh    50-120
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
    Monitor        "Generic Monitor"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Modes        "1280x1024@60"    "1280x960@75"    "1280x960@60"    "1400x1050@60"    "1280x1024@75"    "1600x1200@60"    "1152x864@75"    "1024x768@43"    "1024x768@60"    "1024x768@70"    "1024x768@75"    "1024x768@85"    "832x624@75"    "800x600@60"    "800x600@85"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@85"    "640x480@75"    "640x480@72"    "640x480@60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
    
    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
EndSection
Section "Module"
    Load        "v4l"
EndSection
Section "device" # 
    Identifier    "device1"
    Boardname    "ATI Radeon (vesa)"
    Busid        "PCI:1:0:0"
    Driver        "vesa"
    Screen    1
    Vendorname    "ATI"
EndSection
Section "screen" # 
    Identifier    "screen1"
    Device        "device1"
    Defaultdepth    24
    Monitor        "monitor1"
EndSection
Section "monitor" # 
    Identifier    "monitor1"
    Gamma    1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by nerkman on 2007-10-19
I tried the SKIP_CHECKS and it wouldn't work.  All I got what this:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5960 (rev 01) (prog-if 00 [VGA])
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
```

---

### Post by Forlong on 2007-10-19
You are uzsing the vesa driver.
Change this:
```
    Driver        "vesa"
```
to
```
    Driver        "ati"
```

---

### Post by nerkman on 2007-10-19
Tried that, rebooted.  Still the same.

---

### Post by Forlong on 2007-10-19
Then reset your xorg.conf:
```
sudo dpkg-reconfigure xserver-xorg
```
(choose ati when asked for a driver)

Restart X and If it still doesn't work, try the SKIP_CHECKS thing again.

---

### Post by nerkman on 2007-10-19
Still not working.

Ugh.

---

### Post by DrQuincy on 2007-10-20
> **Forlong said:**
> Who made such statement?

Because such elementary things you possibly could never live without, as desktop effects?

You do know the only people you have to blame here are the ones working for ATI?
Don't blame Linux if it doesn't get proper support by hardware vendors.

I know it's frustrating. I have an ATI myself but I know whose damn fault it is, I can't use Linux' full potential.


Sorry for the rant but please keep in mind that many things just can't be "finished" by Linux/Ubuntu alone.

But to answer your previous question (finally): this How-To makes use of the latests driver provided directly by ATI (and therefore not tested by Ubuntu). I don't know if it's really necessary, though.

Sorry for my rant too - it was in the heating of wasting hours trying to get it working.  While I agree a lot of it is the ATI team rather than Ubuntu I still stad by my annoyance that upgrading to Gutsy broke my resolution that WASN'T using the propritery drivers.

---

### Post by Darkstrike on 2007-10-20
Hello,
I am relatively new to Ubuntu, but I love what it can do. I have followed this How To and am able to go in and enable the Desktop Effects. However as soon as I do, checking either Normal or Extra, My window bars disappear, desktops won't switch, and while the menu still works, nothing else will. 

I am running a Dell Inspiron E1505 with a Radeon X1400.

Wondering if anyone could help me out with this problem, Thanks for all the help so far!

---

### Post by Ub1476 on 2007-10-20
> Hello,
I am relatively new to Ubuntu, but I love what it can do. I have followed this How To and am able to go in and enable the Desktop Effects. However as soon as I do, checking either Normal or Extra, My window bars disappear, desktops won't switch, and while the menu still works, nothing else will.

I am running a Dell Inspiron E1505 with a Radeon X1400.

Wondering if anyone could help me out with this problem, Thanks for all the help so far!

Here's what I did:

Clean install of Ubuntu 7.10
Starts Ubuntu 7.10
Go to System>Administration>Restricted Driver Manager>Enable ATI driver
Next, install XGL: System>Administration>Synaptic>Search for XGL>Install the XGL package.
Search for compiz settings>Install it.
Reboot
Go to: System>Preferences>Appearance>Visual Effects>Normal/ Extra/ Custom.

It's 95% out of the box, didn't even get a X server error!\\:D/


Done with ATI Radeon Mobility X1400 128MB.

---

### Post by ericderace on 2007-10-21
Hi,

I've done exactly your steps and it does work !!  Man, I've been trying to get this to work for days...

Thanks !

I'm using Ubuntu 7.10 on a Thinkpad T60, ATI Radeon X1400 512mb.

---

### Post by Darkstrike on 2007-10-21
Thanks! Did what you said and everything works great!

---

### Post by Rhaddad on 2007-10-22
the x1400 driver is not available anymore?

---

### Post by GordonMorgan on 2007-10-22
Thanks Ub1476 your solution worked 1st time for me, tried others but yours worked a treat  on my acer aspire 5100 (ati Radeon Mobility X1300) :)

---

### Post by jam-2000 on 2007-10-23
"Thanks Ub1476 your solution worked 1st time for me, tried others but yours worked a treat on my acer aspire 5100 (ati Radeon Mobility X1300) "


Sorry for Ctrl+C Ctrl+V (I know English very bad) but when I read post from Ub1476 and decide to try Ub1476's solution I didn't know that this will work and will work so simple & fast :guitar:


So simple method to taste Effects and to increase 3D performance, very BIG Thanks to Ub1476 !!!
	
I write so emotionally because I'm novice in Linux, and for several days trying to resolve the problem with the 3-D performance. read a lot of decisions and has only increased productivity. thought change laptop (bad driver ATI led me to rabies)
and today tried to read this solution to the problem and not believe their eyes of, it works

THANK YOU !!!

My config:
Notebook ASUS  X51R (RadeOn x1100)
glxgears FPS:
   before - 550-600 fps
   middle (only restricted drivers installed) - 1150-1230 fps
   after all - 1800-1890 fps
                 COOOOOOL :)))

---

### Post by nucularbum on 2008-02-12
I have an ATI Mobility Radeon X700 graphics chip, but I presume the procedure detailed in the first post should apply to it as well.

After I execute the command 
```
sudo dpkg -i xorg-driver-fglrx-8.452.1-1_i386.deb fglrx-kernel-source-8.452.1-1_i386.deb
```
I keep getting the error that the kernel cannot be compiled and that fglrx-kernel-source is not installed. I have removed and reinstalled it, still no avail.

Was I supposed to do anything with xorg-driver-fglrx[COLOR="Red"]-dev[/COLOR]_8.452.1-1_i386.deb at all?

On another note, can I totally undo the steps I've followed so far? As this procedure has been tedious and not rewarding, I'm considering just installing the fglrx driver from the repository and I'd rather not have remnants of my previous failed attempts.

---

### Post by rudxai on 2008-02-19
I keep getting an error when i run "sudo module-assistant build,install fglrx" saying it failed to install it giving me options to either:
-VIEW  (Examine the build log file)
-STOP  (Skip and continue with the next operation
-STOP  (Stop processing the build commands

Also, when i restart it's unable to find my graphic card and puts me under 640x resolution!
HELP ??

---

