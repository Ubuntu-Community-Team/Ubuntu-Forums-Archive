---
title: "X not starting again"
date: 2008-01-01
forum: Desktop Environments
---

### Post by zhimsel on 2008-01-01
Hey guys, I have a PC running Ubuntu 7.10 Server. I have IceWM and WDM installed only to configure Azureus (which I have running headless normally). For some reason, when I exit IceWM (or quit X for any reason, such as ctrl+alt+backspace) X does not start again normally. It has just a blank screen. I try switching to runlevel 1 then back to 2, but it still won't start. I am forced to restart in order for X to start again. Can anyone help me fix this problem? I will supply any conf files or command output on request. Thanks!

---

### Post by tgilber1 on 2008-01-01
Please, post your hardware config & /var/log/Xorg.0.log and xorg.conf files

---

### Post by jargoman on 2008-01-01
This will probably work

[http://ubuntuforums.org/showthread.php?t=432503]("http://ubuntuforums.org/showthread.php?t=432503")

---

### Post by zhimsel on 2008-01-01
> **jargoman said:**
> This will probably work
[http://ubuntuforums.org/showthread.php?t=432503]("http://ubuntuforums.org/showthread.php?t=432503")
I do not use gdm, so this does not apply. 

> **tgilber1 said:**
> Please, post your hardware config & /var/log/Xorg.0.log and xorg.conf files

Xorg.0.log, xorg.conf and the output from dmesg are attached (sorry I had to tar them, the logs were too big to upload). I did not build this computer so I don't remember exactly what hardware is in there. To the best of my knowledge: Pentium (I think 4) 2.0GHz, 512MB RAM, Integrated Video (Intel based), Integrated AC'97 Sound (Intel 82801DB-ICH4), I'm not sure on anything else.

---

### Post by tgilber1 on 2008-01-01
The xorg.conf file is configured for the wrong driver (vesa).  You should change it to intel.  According to the dmesg file, you have an Intel 830M chipset.  Hence, why you should change the device driver to "intel"

_extract from your dmesg file below_
agpgart: Detected an Intel 830M Chipset

1.  Install Intel video driver # sudo apt-get install xserver-xorg-video-intel

2.  Change device driver for video card in /etc/X11/xorg.conf

_Example of change to xorg.conf file_
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

3.  Check to make sure BusID is correct, which it should be. # lspci
lspci #check the line labeled 0:2.0, it should have you the Intel vide
o card

4.  Check out xorg.conf for additional settings for 830M card that can be tweaked 
# issue following command "man intel"

5.  Restart XServer using CTRL+ALT+BKSP or restart your computer

Other commands that may help with configuration after booting XServer

sudo xresprobe <driver>  # sudo xresprobe intel

xrandr #

Hope it all works out!

---

### Post by zhimsel on 2008-01-01
> **tgilber1 said:**
> The xorg.conf file is configured for the wrong driver (vesa).  You should change it to intel.  According to the dmesg file, you have an Intel 830M chipset.  Hence, why you should change the device driver to "intel"
///SNIP///

I did exactly as you said, but it still doesn't work. WDM and X load fine at boot, but when I log out of IceWM, instead of going back to the log in screen (wdm) it just goes blank. It also does this when I switch to a terminal (ctrl+alt+f1,f2,etc) and back. It forces me to restart, thus kicking off any users that my be logged in via SSH or FTP.

---

### Post by tgilber1 on 2008-01-01
Please, post the latest Xorg.0.log file when loading the intel driver

---

