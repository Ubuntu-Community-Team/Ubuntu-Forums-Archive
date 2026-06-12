---
title: "Ubuntu 9.04 failing to start GUI"
date: 2009-04-28
forum: Desktop Environments
---

### Post by xblade37 on 2009-04-28
Hi
 
So I decided to take a the plunge and ditch windows vista for ubuntu 9.04. Live CD started ok and I managed to install to the hard disk. Booted up first time fine got to the GUI desktop. I enabled the nvidia drivers and rebooted the system and now I dont get any GUI. I have to resort to terminal 1 window. I have checked the X11 log under /var/log/x11.1.log it says Cannot open display. If I tried to run gnome-session from the command line I get ** (gnome-session:5197): WARNING **: Cannot open display: . Interesting enough it doesn't say which display I would expect to see display:0 for instance. I then remembered that ubuntu has a auto repair feature so I booted into recovery and tried the auto repair which didn't work. I still get the same error. I have also tried running dpkg-reconfigure -phigh xserver-xorg as details in the xorg configure file, it completes ok but still have the same problem. I have to manually type this but here is what my xorg.conf file reads as:
 
Section "Deivce"
Identifier "Configured Video Device"
EndSection
 
Section "monitor"
Identifier "Configured Monitor"
EndSection
 
Section "Screen"
Identifier "Default Screen"
Monitor "configured Monitor"
Device "Configured Video Device"
Endsection
 
 
This is all thats in my config file!! Seems a bit short, I'm used to seeing loads more configuration options in there.
 
Any help would be much appreciated.
 
Cheers
Ray

---

### Post by xblade37 on 2009-04-29
Anyone have an ideas?

---

### Post by StuartN on 2009-04-29
> **xblade37 said:**
> Anyone have an ideas?

Try ```
lshw -C video
``` to find the model and driver of your graphics card, then see if there are forum posts about similar problems - 9.04 has hit some Intel, NVidia and ATI cards.

---

### Post by tkoco on 2009-04-29
Hopefully this info will help:

I found that the "default" methods for the Xorg tend to use the 'most colors', 'highest resolution', etc. Depending on what the capability of your video card is, the "default" setting may exceed what the video card can display. In '/var/log', look for the 'Xorg.0.log' file and read what the Xserver was attempting to do. Generally, if the video hardware is being exceeded, you will see fatal error messages in that logfile. The messages are verbose enough to give you a clue. You may have to hand-craft an 'xorg.conf ' to get around the problem.
 
> **xblade37 said:**
> Hi
 
So I decided to take a the plunge and ditch windows vista for ubuntu 9.04. Live CD started ok and I managed to install to the hard disk. Booted up first time fine got to the GUI desktop. I enabled the nvidia drivers and rebooted the system and now I dont get any GUI. I have to resort to terminal 1 window. I have checked the X11 log under /var/log/x11.1.log it says Cannot open display. If I tried to run gnome-session from the command line I get ** (gnome-session:5197): WARNING **: Cannot open display: . Interesting enough it doesn't say which display I would expect to see display:0 for instance. I then remembered that ubuntu has a auto repair feature so I booted into recovery and tried the auto repair which didn't work. I still get the same error. I have also tried running dpkg-reconfigure -phigh xserver-xorg as details in the xorg configure file, it completes ok but still have the same problem. I have to manually type this but here is what my xorg.conf file reads as:
 
Section "Deivce"
Identifier "Configured Video Device"
EndSection
 
Section "monitor"
Identifier "Configured Monitor"
EndSection
 
Section "Screen"
Identifier "Default Screen"
Monitor "configured Monitor"
Device "Configured Video Device"
Endsection
 
 
This is all thats in my config file!! Seems a bit short, I'm used to seeing loads more configuration options in there.
 
Any help would be much appreciated.
 
Cheers
Ray

---

### Post by xblade37 on 2009-05-01
Thanks for the responses. I have found what appears be the problem. After re-installing a preforming the same actions the problem returned. Installed fresh and enabled the Nvidia drivers. I took another look at my log for xorg, further up about half way I can see that it detects two nvidia cards because I have a SLI system. This is where the problem lies, it says it cannot ID which is the main card, I have altered my configuration to include the PCI:1:0:0 settings. I had to list my pci cards, find the port numbers and include it in my configuration and bam it works. I'll upload my new xorg config so if anyone else is having the same issue. Just gotta figure out how to enable SLI.

Regards

---

### Post by xblade37 on 2009-05-03
So this is my config file once I added my busid, I found this by doing a lspci command.

Section  "Device"
      Identifier    "Configured Video Device"
          Boardname    "nv"
      Busid        "PCI:1:0:0"
      Driver    "nvidia"
          Screen 0
      Option "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
              
EndSection

Section "Module"
    Load    "glx"
EndSection

I'm still trying to get both cards working in SLI but booting my machine into GUI with Nvidia drivers is a start :P

---

### Post by xblade37 on 2009-05-06
After some more investigation it would appear the nvidia restricted drivers marked 'Recommend' as per the restricted driver installer are bugged. I have downgraded to the previous release and now SLI is working and I no longer need to manually alter the xorg.conf file. So anyone else experiencing nvidia restricted drivers is best of installing the previous release.

---

