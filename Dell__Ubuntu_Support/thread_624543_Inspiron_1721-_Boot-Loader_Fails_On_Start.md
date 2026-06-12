---
title: "Inspiron 1721- Boot-Loader Fails On Start"
date: 2007-11-27
forum: Dell  Ubuntu Support
---

### Post by forestcall on 2007-11-27
Hi All :-)

I have a Dell Inspiron 1721 (Wide Sceern with CAM)

I have the Desktop Version  burned to a DVD- 

When I Boot it gets an Error. Something about a missing file and then it goes to a blue and white screen with a message about the Display Server not starting about 6 times in 90 seconds. 

Then it just trys the same thing over and over.

I tested the CD and it tested fine.

Any suggestions?

---

### Post by forestcall on 2007-11-27
BTW - I have AMD- Turion 64

--------------------------------------

What is the difference between Gutsy and Feisty?

Im going to try this now-

Ubuntu 7.04 (Feisty Fawn) PC (Intel x86) install/live DVD

---

### Post by forestcall on 2007-11-27
here is the error i get on boot-

bcm43xx: Error: Microcode "bcm43xx_microcode.fw" not available or load failed

---

### Post by forestcall on 2007-12-05
hello :-)

does anyone know what this means?

thanks

---

### Post by jjustin01 on 2007-12-08
Not why that error would be hanging up your system on start-up.  The bmc reference is your wifi card.  I've installed Ubuntu a few times now on my 1721 with no problems.  My initial problems with Ubuntu's install was with the boot loader not getting installed properly in my MBR, but I was able to fix that.

Since it is a fresh install, I would simply suggest re-installation.  Are you trying to install the 32bit or 64bit version?

The difference between Gutsy and Feisty is minimal.  I personally had better luck getting Gutsy installed with fewer problems then Feisty.

I'm including my own personal walk-through that I've written up for my laptop since I have the tendency to tinker and jack up my install.  This makes it easier for me to avoid searching for the same things over and over.  Using this walk-through I can have Ubuntu installed with everything working within 30 minutes.  Hopefully this will help.

**Desktop Effects**
edit /etc/X11/xorg.conf and change
Section "Extensions"
# Option "Composite" "0"
EndSection

to read
Section "Extensions"
Option "Composite" "1"
EndSection

sudo apt-get install xserver-xgl


**Wifi**
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)


**Ubuntu Splash**
[https://bugs.launchpad.net/ubuntu/+bug/152726](https://bugs.launchpad.net/ubuntu/+bug/152726)
- edit the file: /etc/usplash.conf
- change the resolution inside the conf file
# Usplash configuration file
xres=1280
yres=800
- run: sudo update-initramfs -u



**Ubuntu Login Splash**
Copy desired image to /usr/share/pixmaps/splash and name file "ubuntu-splash.png"
gconf-editor
Go to apps->gnome-settings
Check "show_splash_screen"



**Audio and some other things**
sudo apt-get install linux-backports-modules-generic (actually installs the audio)
[http://ubuntuforums.org/showthread.php?t=577469](http://ubuntuforums.org/showthread.php?t=577469)


**Smooth Fonts (Save to home folder as .fonts.conf)**
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
<edit name="autohint" mode="assign">
<bool>true</bool>
</edit>
</match>
</fontconfig>



**Install MS Fonts**
sudo apt-get install msttcorefonts
sudo fc-cache -fv


**Install Avant Window Navigator**
[http://wiki.awn-project.org/index.php?title=DistributionGuides](http://wiki.awn-project.org/index.php?title=DistributionGuides)


**Backspace in Firefox fix**
URL - about:config
filter for "backspace" and change option to 0


**Adjust Mouse settings**
sudo apt-get install qsynaptics
sudo apt-get install synclient (Not necessary if the following xorg.conf changes are made)

Edit the Mouse section of /etc/X11/xorg.conf to look like the following:

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "on"
        Option          "PressureMotionMinFactor" "2.7"   
        # When finger pressure drops below this value,
    # the driver counts it as a release.
    Option        "FingerLow"             "14"
    # When finger pressure drops below this value,
    # the driver counts it as a release.
    Option        "FingerHigh"            "15"
    # max. time (in milliseconds) for detecting a tap
    Option        "MaxTapTime"            "180"
    # max. movement of the finger for detecting a tap
    Option        "MaxTapMove"            "110"
EndSection



**In case Grub does not install properly, go here and install EasyBCD to setup Vista’s boot loader for dual boot**
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
[http://neosmart.net/downloads/software/EasyBCD/EasyBCD%201.7.exe](http://neosmart.net/downloads/software/EasyBCD/EasyBCD%201.7.exe)


Speed up Firefox
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

