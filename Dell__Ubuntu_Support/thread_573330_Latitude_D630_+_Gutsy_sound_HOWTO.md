---
title: "Latitude D630 + Gutsy sound HOWTO"
date: 2007-10-11
forum: Dell  Ubuntu Support
---

### Post by gdanko on 2007-10-11
I've seen a number of posts about this on the internet. Now I have it working.

_Sound Support_

Install the utilities needed to configure the kernel
[INDENT][FONT="Courier New"]sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev
[/FONT][/INDENT]
Move to the configuration directory
[INDENT][FONT="Courier New"]cd /usr/src[/FONT][/INDENT]

Make yourself the omnipotent root
[INDENT][FONT="Courier New"]sudo -s[/FONT][/INDENT]

Now we are going to download the kernel and unpack it
[INDENT][FONT="Courier New"]wget [http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.tar.bz2)
tar -xvjf linux-2.6.23.tar.bz2[/FONT][/INDENT]

Remove the link to the linux directory, make a new link to the new kernel, and move to the Linux directory
[INDENT][FONT="Courier New"]rm -rf linux
ln -s /usr/src/linux-2.6.23 linux
cd /usr/src/linux
[/FONT][/INDENT]

Now import your current kernel configuration and get your current kernel options (accept all the defaults here)
[INDENT][FONT="Courier New"]cp /boot/config-`uname -r` .config
make oldconfig[/FONT][/INDENT]

Configure the kernel
[INDENT][FONT="Courier New"]make menuconfig[/FONT][/INDENT]
Navigate to *Device Drivers > Sound > Advanced Linux Sound Architecture > PCI Devices*. Select *Intel HD Audio* and press M.
That's it! Save your kernel config.

Finally, it's time to build the kernel: Make sure that you are in /usr/src/linux with full root access. This will build a debian file that you can install
[INDENT][FONT="Courier New"]make-kpkg clean
make-kpkg -initrd --revision=386 kernel_image kernel_headers modules_image[/FONT][/INDENT]

Install the .deb files in /usr/src. There should be 2. One should be an image .deb file and the other a header .deb file. In terminal do
[INDENT][FONT="Courier New"]cd .. && dpkg -i linux*.deb[/FONT][/INDENT]

REBOOT

The kernel rebuild HOWTO came from [http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel]("http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel")

_Fix WiFi_
Install the bcm43xx-fwcutter package
[INDENT][FONT="Courier New"]apt-get install bcm43xx-fwcutter[/FONT][/INDENT]

Download the driver
[INDENT][FONT="Courier New"]wget [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)[/FONT][/INDENT]

Extract the firmware
[INDENT][FONT="Courier New"]sudo bcm43xx-fwcutter -w /lib/firmware  wl_apsta-3.130.20.0.o[/FONT][/INDENT]

REBOOT

When you come back you should now have sound and wifi

---

### Post by r76 on 2007-10-13
Well the sound worked - but after the reboot the video card was not recognised and I got stuck with 640x480 video in VESA after all that :(

I'd rather have the sound.  Also, my D630 runs openSUSE 10.3 and sound isn't an issue - I believe that's a 2.6.22 kernel like Gutsy, so should 2.6.23 be necessary?  Fortunately I got the intel 3945 wireless, so that wasn't a problem.

---

### Post by gdanko on 2007-10-13
Hmm mine came back up at 1440x900 with the nv driver. Try just reconfiguring X. There's a command you can use in dpkg to configure this stuff. Should work like a champ.

---

### Post by rhanka on 2007-10-16
That's ok for the sound...

But I didn't get the wifi at all ?

---

### Post by gdanko on 2007-10-16
From my original document.

Fix WiFi
Install the bcm43xx-fwcutter package

    apt-get install bcm43xx-fwcutter

Download the driver

    wget [http://downloads.openwrt.org/sources...a-3.130.20.0.o](http://downloads.openwrt.org/sources...a-3.130.20.0.o)

Extract the firmware

    sudo bcm43xx-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o

REBOOT

---

### Post by chieferer on 2007-10-17
Nice!  The Audio worked for me thank you :):).  Didnt try the Wifi

---

### Post by gdanko on 2007-10-18
> **chieferer said:**
> Nice!  The Audio worked for me thank you :):).  Didnt try the Wifi

Glad I could help!

---

### Post by wty on 2007-10-19
I got the sound working, but the display is a bitt off. And I can't (of course) use linux-restricted since the new kernel needs linux-recstricted-modules-2.6.23 :\ 

and that really really sucks..

---

### Post by gdanko on 2007-10-19
A few people have fussed about this. I had no problems with video after reboot. However, you can rebuild your X config with this command..

sudo dpkg-reconfigure xserver-xorg

---

### Post by SnappyCrunch on 2007-10-19
[COLOR="Gray"]Thanks! Both my sound and my wireless work great!

I had to reinstall the driver to my Nvidia Quadro NVS 135M, but I have to do that every time I update my kernel. For those who don't know, the offical Nvidia driver can be found at [http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html)

I appreciate the flawless instructions![/COLOR]
------------------------------------------------------------------------------------------------------------------

**EDIT**

It turns out that a kernel recompile isn't necessary. The [Laptop Testing Team]("https://wiki.ubuntu.com/LaptopTestingTeam") reports that for the [Latitude D630]("https://wiki.ubuntu.com/LaptopTestingTeam/Dell/DellLatitudeD630"), you just need to follow method G on [this]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") Ubuntu Wiki page. Getting wireless working after that (if you have the Dell 1390 card) is just a matter of following the instructions in the Restricted Drivers Manager (System -> Administration -> Restricted Drivers Manager).

If you still want to install the Nvidia driver from the Nvidia website rather than just going through the Restricted Drivers Manager (They *should* be the same thing, but I can't confirm that), then you'll need to disable the open source "nv" driver. To do that, you'll need to add the line "DISABLED_MODULES="nv"" to /etc/default/linux-restricted-modules-common.

---

### Post by gdanko on 2007-10-19
Hmm I haven't been able to get the NVidia drivers working. I downloaded the .run file, booted, exited gdm, etc etc, but after installing them I reboot to be sure and I get some low graphics mode.. VESA.. and the driver will not come up.

Any help is appreciated.

---

### Post by SnappyCrunch on 2007-10-19
> **gdanko said:**
> Hmm I haven't been able to get the NVidia drivers working. I downloaded the .run file, booted, exited gdm, etc etc, but after installing them I reboot to be sure and I get some low graphics mode.. VESA.. and the driver will not come up.

Any help is appreciated.

**EDIT**
I found the solution. You need to add the line ```
DISABLED_MODULES="nv"
``` to ```
/etc/default/linux-restricted-modules-common
``` to disable the open source "nv" driver. If it's still there, it conflicts somehow with the new "nvidia" driver, and causes the system to run in failsafe mode.

**/EDIT**


[COLOR="Gray"]This really should have a new thread, but here goes. Check your xorg.conf file. A copy of mine is below. DO NOT just replace your xorg.conf with this one. Study this one to see how it's different from yours. I created that to my liking back when Gutsy was still in beta, so the current defaults might be different/better. The "Screen" section and the "Monitor" are of particular interest, and the "InputDevice" section regarding the Synaptics Touchpad has a few variables that control the mouse speed which you may want to change.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
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
    Option         "SHMConfig" "true"
    Option         "MaxSpeed" "0.99"
    Option         "AccelFactor" "0.08"
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
    HorizSync       28.0 - 72.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
#	Option "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1280x800" "1024x768" "800x600"
    EndSubSection
EndSection

```[/COLOR]

---

### Post by gdanko on 2007-10-19
I got some sort of error that hinted the system couldn't load the driver.

---

### Post by modulok on 2007-10-19
I went through the sound part, everything seemed like it worked, rebooted and sound still doesn't work.

what information do you need to lend me some help?
thanks

---

### Post by mflowj on 2007-10-20
This works fine:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa


--Dell 630 + Gusty

---

### Post by gdanko on 2007-10-20
> 
This works fine:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa


Does this work with the out of the box kernel?

---

### Post by SnappyCrunch on 2007-10-20
> **gdanko said:**
> I got some sort of error that hinted the system couldn't load the driver.
[COLOR="Gray"]
Well, let's get the obvious out of the way. Are you sure you have a D630 with the Nvidia Quadro NVS 135M chipset? Have you used all the defaults in the driver installation, including allowing it to create a new xorg.conf file? What is the exact error message? What are the contents of your xorg.conf file?[/COLOR]
**EDIT**
As I've said in previous edits in this thread, it turns out the correct solution is to add the line "DISABLED_MODULES="nv"" to /etc/default/linux-restricted-modules-common
**/EDIT**

---

### Post by mflowj on 2007-10-20
> **gdanko said:**
> Does this work with the out of the box kernel?

Yep I dont touch the kernel.

---

### Post by jarubio on 2007-10-20
> **mflowj said:**
> This works fine:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa


--Dell 630 + Gusty


I used this on my Dell Latitude D830 for the sound, it worked like a charm after reboot.

---

### Post by bluedragon436 on 2007-10-21
I have a D610 and tried to give this a try also and then restarted my computer and I still have no real sound...I get sound when I first log on, and that is about it...  Also now once I log in it hangs up for a few where as it didn't do that before.  I guess this is one of those bugs u just kind of have to play and adjust until it is perfect.  Now I also have no control over my volume unless I open the volume control panel and manually adjust it.

---

### Post by SnappyCrunch on 2007-10-21
> **bluedragon436 said:**
> I have a D610 and tried to give this a try also and then restarted my computer and I still have no real sound...I get sound when I first log on, and that is about it...  Also now once I log in it hangs up for a few where as it didn't do that before.  I guess this is one of those bugs u just kind of have to play and adjust until it is perfect.  Now I also have no control over my volume unless I open the volume control panel and manually adjust it.

The D610 is completely different from the D630. I highly doubt it has the same audio chipset.  You should go back to the standard kernel until you can compile a kernel with the correct driver for your laptop.

---

### Post by stevie_velvet on 2007-10-30
> **jarubio said:**
> I used this on my Dell Latitude D830 for the sound, it worked like a charm after reboot.

No dice for my D830
nothing on #lspci either..sound fine on windows

May have to perform a kernal upgrade

---

### Post by ozp on 2007-11-13
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Method G worked for me

But the sound sound like bad quality (I dont know if is the software sound or hardware problem - speaker)

What deal is the best? Method G or this?

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Will be good or bad to perform method G and this deal above?

---

### Post by ruffwuk on 2007-12-04
I have a dell Latitude D 630 with the Intel sound card:
just do this
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Reboot computer and it's perfect

I got it from the D830 with the same sound issue.

---

### Post by blidmen on 2007-12-27
Hello,
my Dell Latitude D630 works fine except:

- microphone doesn't work
- bluetooth led is on but doesn't work (but an external USB BT adapter  works fine immediately)
- the led of WiFi is off, but WiFi works fine
Any suggestion?
The most annoising problem is the impossibility to use programs like skype, ekiga ... because of the mic: any suggestion for this point is greatly appreciated
Thanks!

---

### Post by JHavel on 2007-12-27
> **blidmen said:**
> Hello,
my Dell Latitude D630 works fine except:

- microphone doesn't work
- bluetooth led is on but doesn't work (but an external USB BT adapter  works fine immediately)
- the led of WiFi is off, but WiFi works fine
Any suggestion?
The most annoising problem is the impossibility to use programs like skype, ekiga ... because of the mic: any suggestion for this point is greatly appreciated
Thanks!

Hallo,
I'm new to linux, to ubuntu etc. after instalation I had the sound problems / I,ve tried all I read / the soud is OK, but the microphone still does'nt work, I need it for Skype. If anybody can help / would be great. Thanks. Jan
:)

---

### Post by adrian.oneclick on 2007-12-31
> **JHavel said:**
> Hallo,
I'm new to linux, to ubuntu etc. after instalation I had the sound problems / I,ve tried all I read / the soud is OK, but the microphone still does'nt work, I need it for Skype. If anybody can help / would be great. Thanks. Jan
:)

same problem :( someone pls help :-*

---

### Post by rancor on 2008-01-06
> **blidmen said:**
> Hello,
my Dell Latitude D630 works fine except:

- microphone doesn't work
- bluetooth led is on but doesn't work (but an external USB BT adapter  works fine immediately)
- the led of WiFi is off, but WiFi works fine
Any suggestion?
The most annoising problem is the impossibility to use programs like skype, ekiga ... because of the mic: any suggestion for this point is greatly appreciated
Thanks!

I have the 64-bit version and I have tried this but the sound does still not work.

Do you folx run 32- or 64-bit system?

// rancor

---

### Post by jkildea on 2008-01-11
I have this same problem. I have sound fine but no microphone which I really need for skype.

Thank you!

---

