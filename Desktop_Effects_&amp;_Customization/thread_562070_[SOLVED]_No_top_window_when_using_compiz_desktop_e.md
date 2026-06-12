---
title: "[SOLVED] No top window when using compiz desktop effects"
date: 2007-09-28
forum: Desktop Effects &amp; Customization
---

### Post by Newbie1978 on 2007-09-28
Hello, I'm completed beginner in Linux but I consider myself to be quite knowledgeable in Windows but Vista was too much for me that OS is so bad that make run to Linux looking for a stable OS that also can bring good desktop effects to the user.

AFTER INSTALLATION UBUNTU ULTIMATE WORKS FINE, BUT WHEN I TRY TO ENABLE DESKTOP EFFECTS THE TOP OF EACH  WINDOWS DISAPPEAR, I TRY LOTS OF THINGS WITH NO RESULTS. PLEASE HELP 

My specs are:

Processor AMD Athlon 64 X2 TK-53 1.7 GHZ
HARD DRIVE 120 GB Serial ATA hard drive
1 GB RAM (2 GB max),
MASHITA 8x DVD-/+RW drive ATA device
Connectivity: 3 USB, 1 FireWire, 1 VGA, 1 S-Video, expansion port 3 connector, ExpressCard 54/34, 5-in-1 memory card reader
54g Wi-Fi LAN (802.11b/g), 10/100 Ethernet
Nvidia GeForce Go 6150 video card with up to 287 MB shared memory
Pre-installed with Windows Vista Home Premium 32 BIT OS

Section "Monitor"
Identifier "Generic Monitor"
HorizSync 28.0 - 64.0
VertRefresh 43.0 - 60.0
Option "ForceDevice" ISDV4"

Section "Device"
Identifier "nVidia corporation C51 [Gerforce 6150 Go]"
Driver "nVidia"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "nvidia Corporation C51 [Gerforce 6150 Go]
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
modes "1280x800
EndSubsection
SubSection "Display"
Depth 4
modes "1280x800
EndSubsection
SubSection "Display"
Depth 8
modes "1280x800
EndSubsection
SubSection "Display"
Depth 15
modes "1280x800
EndSubsection
SubSection "Display"
Depth 16
modes "1280x800
EndSubsection
SubSection "Display"
Depth 24
modes "1280x800
EndSubsection

---

### Post by FuturePilot on 2007-09-28
Add these two lines to the Device section in your xorg.conf
```
 Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"

```
Log out and restart X with Ctrl+Alt+Backspace

---

### Post by Newbie1978 on 2007-09-28
> **FuturePilot said:**
> Add these two lines to the Device section in your xorg.conf
```
 Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"

```
Log out and restart X with Ctrl+Alt+Backspace

Hello!! thanks for reply to the thread, I use this with no results maybe I'm doing it wrong would you please explained it to me with more details where do I write the line above? and how do I reset the xserver? I always end up with an xserver configuration error and eventually have to hard reset,  I'm just a beginner that would really likes to enjoy the compiz fusion, I try my best to follow the instructions. Thank you so much for the info

---

### Post by FuturePilot on 2007-09-28
I[m guessing you have installed the Nvidia driver with the Restricted Driver Manager. If you haven't you can find it in System>Administration>Restricted Driver Manager. If you have already done that then let's edit xorg.conf
```
gksudo gedit /etc/X11/xorg.conf
```
Go down and find the Device section. You should see something like this 

```
Section "Device"
Identifier "nVidia corporation C51 [Gerforce 6150 Go]"
Driver "nVidia"
EndSection
```
Just add those two lines to this section so it looks like this
```
Section "Device"
Identifier "nVidia corporation C51 [Gerforce 6150 Go]"
Driver "nVidia"
[COLOR="Red"] Option          "AddARGBVisuals"        "True"
 Option          "AddARGBGLXVisuals"     "True"[/COLOR]
EndSection
```
You also might want to make sure nvidia is all lowercase for where it says driver.
Save the file, then log out. At the login screen press Ctrl+Alt+Backspace and it will restart Xserver.

---

### Post by Newbie1978 on 2007-09-29
Thank you very much for the help, I will try those detail instruction later, I've being loosing my mind over this for a couple of days now. Thanks again for all the help : (

---

### Post by JBAlaska on 2007-09-29
if that does not work;
open a terminal and type;

sudo apt-get install emerald <enter>


after it installs, 
emerald --replace <enter>

---

### Post by Newbie1978 on 2007-09-30
Hay every body thank you so much for the help!!!!!!!!!!!!!! I use this simple steps and bingo got to work pretty quick I may add, it seems so simple now but sure I have a lot of frustration while trying to get it up and running 
 
sudo aptitude install emerald emerald-themes  

compiz --replace emerald

---

