---
title: "Suspend on a Vostro"
date: 2007-08-11
forum: Dell  Ubuntu Support
---

### Post by aldenhg on 2007-08-11
Hey everyone-
I've got my new Vostro 1400 all set up and rockin' hard, but I can't get Suspend or Hibernate to work properly. For some reason advanced power management issues have always escaped me - even on two other Ubuntu desktops. Anyhow, I have absolutely no idea where to start. When I suspend the computer it seems to go down just fine, but then when I try and wake it up the screen stays black and after 30-45 seconds it starts beeping loudly, at which point I generally freak out a little bit and turn it off manually. When I try and hibernate it once again goes down just fine, but then upon powering it back up it just starts up as normal. 
Anyhow, where should I start? What logfiles should I post?


EDIT:


I fixed it! Note that this is specific to the Dell Vostro 1400 with the Nvidia 8400M GS. It should work on other Dells of the same lineage with the same chipsets, but I make no guarantees. You should also keep in mind that I do not in fact know what I'm doing so if you bork your machine following my instructions I'll try and help you out of it, but I can't make any promises. Now, with all that negativity aside, let's move on.
Here's how I got it to work. First open up your /etc/X11/xorg.conf file and add ```
Option     "NvAGP"     "1"
```
in the Device section that also has the name of your video driver.
Second, open up /etc/default/acpi-support and make sure that the following options look like mine: ```
# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
 SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false
```
Third, open up /etc/modules and put nvidia at the top of the list. From what I can tell, this makes it so when the system comes out of suspend it loads up the nvidia driver first which for some reason makes everything play nice. Save your work and reboot. Once you're back up give suspend a try. Marvel for a minute or two at your slow-blinking suspend light and then hit the power button. If it worked then yay! If not, sorry. As I said above, I don't know what I'm doing. Post your problems here and I'll see what I can do and hopefully other people will help as well.
A few things that might happen: Your animated Notification Area icons may look a little screwy. I know there's a fix out there that probably just involves reloading things like the Network Monitor on wake up. If anyone knows how, please enlighten me. Also, I get a white box that just sits there and doesn't do anything that I can't figure you how to kill. I get the feeling it has something to do with the login process, but as long as I put it on one of the other cube faces it doesn't bother me.

---

### Post by ayu on 2007-08-12
> **aldenhg said:**
> Hey everyone-
I've got my new Vostro 1400 all set up and rockin' hard, but I can't get Suspend or Hibernate to work properly. For some reason advanced power management issues have always escaped me - even on two other Ubuntu desktops. Anyhow, I have absolutely no idea where to start. When I suspend the computer it seems to go down just fine, but then when I try and wake it up the screen stays black and after 30-45 seconds it starts beeping loudly, at which point I generally freak out a little bit and turn it off manually. When I try and hibernate it once again goes down just fine, but then upon powering it back up it just starts up as normal. 
Anyhow, where should I start? What logfiles should I post?

Yup, I am also very interested in getting this fixed, although it seems like with all its problems it might be quicker to just do a clean boot than resume from hibernation!  I've got hibernation working... ONCE :p.  It took as much time as a clean boot to resume, and at that point I only had wireless installed after a clean install.  After upgrading to 2.6.0-16, downloading nvidia graphics, fixing the sound and adding scrolling to the touchpad, hibernation never worked again.  The screen and wireless LED will turn off, but the power indicator and fan is still on.  Can't resume from standby.  Hope somebody here knows what to do! :)

---

### Post by aldenhg on 2007-08-12
I figure it might be worth mentioning that I'm running the 2.6.20-15-generic kernel. I'm not sure if it makes a diffrenence or not, but it couldn't hurt. I also use the ndiswrapper and kqemu modules.

---

### Post by ayu on 2007-08-12
> **aldenhg said:**
> 

EDIT:

I fixed it! Note that this is specific to the Dell Vostro 1400 with the Nvidia 8400M GS. It should work on other Dells of the same lineage with the same chipsets, but I make no guarantees. You should also keep in mind that I do not in fact know what I'm doing so if you bork your machine following my instructions I'll try and help you out of it, but I can't make any promises. Now, with all that negativity aside, let's move on.
Here's how I got it to work. First open up your /etc/X11/xorg.conf file and add ```
Option     "NvAGP"     "1"
```
in the Device section that also has the name of your video driver.
Second, open up /etc/defaults/acpi-support and make sure that the following options look like mine: ```
# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
 SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false
```
Third, open up /etc/modules and put nvidia at the top of the list. From what I can tell, this makes it so when the system comes out of suspend it loads up the nvidia driver first which for some reason makes everything play nice. Save your work and reboot. Once you're back up give suspend a try. Marvel for a minute or two at your slow-blinking suspend light and then hit the power button. If it worked then yay! If not, sorry. As I said above, I don't know what I'm doing. Post your problems here and I'll see what I can do and hopefully other people will help as well.
A few things that might happen: Your animated Notification Area icons may look a little screwy. I know there's a fix out there that probably just involves reloading things like the Network Monitor on wake up. If anyone knows how, please enlighten me. Also, I get a white box that just sits there and doesn't do anything that I can't figure you how to kill. I get the feeling it has something to do with the login process, but as long as I put it on one of the other cube faces it doesn't bother me.

Cool!  I will try that later when I have the time and after I get the other things working.  By the way, do you mind posting where you got that info from?  Is it really a fix or more of a "workaround?"  Thanks!

---

### Post by aldenhg on 2007-08-12
I'd call it more of a 'fixaround' then anything. I wish I had kept track now, but this is a mix of advice for a bunch of different recent Dell laptops that I found from the Dell website, launchpad entries and the forums here. I'm not even sure that all the steps are necessary. Editing the acpi-support file seems to be the most important step. I came to the concoction of trues and falses that I did by about half an hour of guess and check.
Also, you're going to run into problems if you suspend often. after the second or third time it always seems to start messing up. It's gotten to the point where after a few cycles I'll have  to go to one of the other terminals, telinit down to runlevel 1 and then switching it back up to 3. Even after that it will still mess up if I suspend again and it seems like the only way to make it suspend well again is to reboot - which kinda undoes all the magic of suspend. I'm working on a fix but I'm also tired of wrestling with it, so don't hold your breath.

---

### Post by Jengu on 2007-08-13
I'm not running compiz, but on gutsy your instructions worked perfectly for me. I haven't tried suspending multiple times yet though :)

Does suspend work out of the box with the nvidia binary driver for any laptops? How about if you buy the dell 1420 w/ ubuntu preloaded?

---

### Post by aldenhg on 2007-08-13
The 1420 and the Vostro 1400 are pretty much the same computer. I guess it might be worth getting someone with and Inspiron to post all of their suspend related files to try and fix this.  I just noticed today that sound doesn't always work after a suspend, so there's clearly a ways to go yet.

---

### Post by daageep on 2007-08-14
My 1400 is coming today. Please keep this thread alive as I never got suspend working on any of my comps either!

---

### Post by aldenhg on 2007-08-15
I'm still having problems. I sometimes can't use sound, the network is sometimes screwy and sometimes it flat out crashes. Anyone have any ideas?

---

### Post by Jengu on 2007-08-15
Has anyone tried suspend with the builtin nv driver rather than the binary nvidia one? Or a build of noveau? Even if it's 2D only, it'd be nice if that worked.

---

### Post by aldenhg on 2007-08-15
I haven't. I like Compiz Fusion way too much. There's nothing quite like a spinning cube, falling rain and windows that close into a puff of brightly colored particles to give some "wow" factor to my clients.

---

### Post by muadnu on 2007-08-18
Somehow, after trying this for the third or fourth time, it worked... Thanks!

A question, though... I'm using dual monitors (with Twinview - Nvidia 8400 GS), and when I come back from suspending, I just get output on my external monitor, and I have to mess for a good while with the Nvidia settings manager to get my configuration back. Just in case, here's my xorg file:

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:40:26 PDT 2007
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG L1732TQ"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M GS"
	Option		"NvAGP"		"1"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +1440+0, DFP: nvidia-auto-select +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by amber_474 on 2007-09-04
> **aldenhg said:**
> Hey everyone-
I've got my new Vostro 1400 all set up and rockin' hard, but I can't get Suspend or Hibernate to work properly. For some reason advanced power management issues have always escaped me - even on two other Ubuntu desktops. Anyhow, I have absolutely no idea where to start. When I suspend the computer it seems to go down just fine, but then when I try and wake it up the screen stays black and after 30-45 seconds it starts beeping loudly, at which point I generally freak out a little bit and turn it off manually. When I try and hibernate it once again goes down just fine, but then upon powering it back up it just starts up as normal. 
Anyhow, where should I start? What logfiles should I post?


EDIT:


I fixed it! Note that this is specific to the Dell Vostro 1400 with the Nvidia 8400M GS. It should work on other Dells of the same lineage with the same chipsets, but I make no guarantees. You should also keep in mind that I do not in fact know what I'm doing so if you bork your machine following my instructions I'll try and help you out of it, but I can't make any promises. Now, with all that negativity aside, let's move on.
Here's how I got it to work. First open up your /etc/X11/xorg.conf file and add ```
Option     "NvAGP"     "1"
```
in the Device section that also has the name of your video driver.
Second, open up /etc/defaults/acpi-support and make sure that the following options look like mine: ```
# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
 SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false
```
Third, open up /etc/modules and put nvidia at the top of the list. From what I can tell, this makes it so when the system comes out of suspend it loads up the nvidia driver first which for some reason makes everything play nice. Save your work and reboot. Once you're back up give suspend a try. Marvel for a minute or two at your slow-blinking suspend light and then hit the power button. If it worked then yay! If not, sorry. As I said above, I don't know what I'm doing. Post your problems here and I'll see what I can do and hopefully other people will help as well.
A few things that might happen: Your animated Notification Area icons may look a little screwy. I know there's a fix out there that probably just involves reloading things like the Network Monitor on wake up. If anyone knows how, please enlighten me. Also, I get a white box that just sits there and doesn't do anything that I can't figure you how to kill. I get the feeling it has something to do with the login process, but as long as I put it on one of the other cube faces it doesn't bother me.

I have a vostro 1400 with Nvidia 8400 card. I tried the above solution and it worked for me. I didn't add:

Option NvAGP = 1 
# to /etc/X11/xorg.conf

But I noticed that wireless network was not coming up from suspend. For which I used the following fix:

# vim  /etc/acpi/resume.d/62-ifup.sh

so that it looks like:

#!/bin/sh

# Bring up the interfaces (this should probably be left up to some policy
# manager, but at the moment we just bring back whatever we ifdowned)

# set the names of your wireless and ethernet interfaces
INTERFACES = "eth0 eth1"
for x in $INTERFACES; do
    ifup $x &
done

---

### Post by amber_474 on 2007-09-05
Well, using the above method, I got suspend to work properly
but hibernate is not working at all. It hangs while hibernating.

---

### Post by .exe on 2007-09-07
Thanks for the guide, it works!

Just a note to make this more copy-paste friendly, in your guide you have the path listed as */etc/defaults/acpi-support*, but the actual path is */etc/default/acpi-support*. So just drop the s off of dfault.

---

### Post by aldenhg on 2007-09-09
@.exe
Thanks. I'll make the change.

---

### Post by MikeRussell on 2007-09-09
Hey guys,

   Just a quick question.  Running Gutsy on an Inspiron 1420 w/ the 8400GS.  Have followed all the proposed changes from above, but X still hangs on resume.  Ctrl-Alt-Backspace forces an X reboot and all is well, but does anyone else have this issue?  Prior to this I had an Inspiron 8600 w/ the Nvidia 5200, and these same options worked perfectly.  Any suggestions?  Thanks!
Mike

---

### Post by MikeRussell on 2007-09-12
**bump**

---

### Post by muadnu on 2007-09-13
I'm getting a blank screen after resuming as you... Have you tried hitting Ctrl+Alt+F1 and then getting back with Ctrl+Alt+F7. That brings X back for me, though most of the time the video works so slow that I have to restart X anyway. Has anyone got suspend to really work with the Vostro 1400 and Nvidia 8400 GS?

---

### Post by aldenhg on 2007-09-13
I've kinda stopped trying. It works well enough for me, so I'm happy. Besides, it starts up fgast enough for my purposes, so I don't even suspend that often.

---

### Post by tclineks on 2007-09-26
For vostro's with Nvidia 8400M cards see [http://ubuntuforums.org/showthread.php?p=3429739](http://ubuntuforums.org/showthread.php?p=3429739)

Mostly solved for me with new Nvidia driver (100.14.19)

Sound still iffy on resume from disk.

---

### Post by dahlheim on 2007-10-01
yay!  worked for me on an xps-m1210.  thanks!  (previously was only able to suspend using stock nv driver)

---

### Post by fak3r on 2007-10-11
This works on the Vostro 1500 with nVidia 8400gs in Gusty!

---

### Post by skorch on 2007-11-04
Worked perfectly for me.  Thanks a bunch!  Not having suspend working was a serious annoyance.

Vostro 1700 w/ NVidia 8600M GT

---

### Post by besada on 2007-11-05
This is on an HP, but maybe it will help you.

[http://ubuntuforums.org/showthread.php?t=602806](http://ubuntuforums.org/showthread.php?t=602806)

---

