---
title: "Resolution problem"
date: 2009-08-12
forum: Desktop Environments
---

### Post by Ricky1 on 2009-08-12
Hi..so i installed ubuntu with 0 problems so far and am loving it but i have a minor problem if someone can help me with it would be so great:)

am using a Nvidia 8500GT card with Driver Version:180.44.....and i was wondering how can i set my resolution to 1280x1024 as am used to that on my windows..but i can't find it on the resolution list,so is there a way to add it manually with terminal or something?

1 more thing is when i click on System>pref>Display i get this msg:
It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?....when i click ok it brings up nvidia x server settings.

do i have to do something to stop this message?or is it fine?

also am using compiz fusion with full settings no i guess my graphics card is fine just want to set this resolution thing..thnx=)

---

### Post by realzippy on 2009-08-12
As using the nvidia driver you have to set your resolution with 
nvidia-settings.Please open terminal and type:

**gksudo nvidia-settings**

Choose desired resolution and do NOT forget to hit:

"save to X configuration file" before closing.

---

### Post by Ricky1 on 2009-08-12
thanks for rply but i already know that...and the problem is i can't find the option 1280x1024 in the list the highest i can choose from is 1360x768 and i want 1280x1024 can i add it manualy?

---

### Post by realzippy on 2009-08-12
You can add a modline in your /etc/X11/xorg.conf.

Open a terminal and type:

**gtf 1280 1024 85**

what gives you a modline to copy in your xorg.conf
Note that 85 is the refreshrate.If its no crt you should set it to 60...

---

### Post by realzippy on 2009-08-12
If you have questions concerning xorg.conf read the manpages:

**man xorg.conf**

..interesting for you is the monitor section where all is said about modelines.

To edit xorg.conf:

**gksudo gedit /etc/X11/xorg.conf**

if problems post your xorg monitor section...

---

### Post by Ricky1 on 2009-08-12
thanks again i used the command and i got this # 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 159.36 MHz
  Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync


sry for the newbie question but where exactly should i put this line in the xorg.conf file?i never used it before.

here it is #   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by realzippy on 2009-08-12
Modeline "1280x1024_85.00" 159.36 1280 1376 1512 1744 1024 1025 1028 1075 -HSync +Vsync
 has to be copied in monitor section:

Section "Monitor"
Identifier "Configured Monitor"
[COLOR="YellowGreen"]Modeline "1280x1024_85.00" 159.36 1280 1376 1512 1744 1024 1025 1028 1075 -HSync +Vsync[/COLOR]
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
EndSection

Section "Module"
Load "glx"
EndSection

Section "Device"
Identifier "Configured Video Device"
Option "UseFBDev" "true"
Driver "nvidia"
Option "NoLogo" "True"
EndSection

---

### Post by realzippy on 2009-08-12
I just see you made a xorg.conf reset by:
sudo dpkg-reconfigure -phigh xserver-xorg

So back to step1:

**gksudo nvidia-settings**

choose a resolution that works,apply,save to X configuration file.
exit nvidia-settings.
Open new xorg.conf:

**gksudo gedit /etc/X11/xorg.conf**

And post again..

---

### Post by P4man on 2009-08-12
Please, **gk**sudo, not sudo for graphical apps..
Next person to suggest "sudo some-x-app" should be forced to reply for a month to all "I suddenly cant log in anymore" threads caused by it :)

---

### Post by realzippy on 2009-08-12
> **P4man said:**
> Please, **gk**sudo, not sudo for graphical apps..
Next person to suggest "sudo some-x-app" should be forced to reply for a month to all "I suddenly cant log in anymore" threads caused by it :)

:redface:
your right.Hope he is in real life;not sitting around without X due to sudo...
btw,for me it never did any harm...

---

### Post by P4man on 2009-08-12
I almost gave up on ubuntu because I kept having problems like "bash: permission denied", some .dmrc or .Xauthority problems. I was so frustrated, and they always came back. Until one day I learnt I shouldn't use sudo nautilus like i always did. I had been using ubuntu for like 6 months and hadn't even *heard* of gksudo.

Anyway, I leant my lesson and hope others don't have to learn it my way, thats why im rather insistent on this issue :)

Sorry for going OT .

---

### Post by realzippy on 2009-08-13
> **realzippy said:**
> I just see you made a xorg.conf reset by:
sudo dpkg-reconfigure -phigh xserver-xorg

So back to step1:

**gksudo nvidia-settings**

choose a resolution that works,apply,save to X configuration file.
exit nvidia-settings.
Open new xorg.conf:

**gksudo gedit /etc/X11/xorg.conf**

And post again..

....or just put this line in your xorg.conf in the "screen" section:

        [COLOR="Lime"]Option"metamodes" "1280x1024_85 +0+0; nvidia-auto-select +0+0" [/COLOR]

so it looks similar to:

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x1024_85 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

This should work.The modeline you generated and put in the "monitor" section can be deleted,although it does no harm..
Restart Xserver...

---

