---
title: "[SOLVED] 9400GT Stuck at 1024*768"
date: 2008-12-26
forum: General Help
---

### Post by Jiffyman on 2008-12-26
I posted this in another section of the forums and it keeps getting knocked three pages back within a matter of hours. So I'm reposting here in hope of getting an answer

The original is here: [http://ubuntuforums.org/showthread.php?t=1021484](http://ubuntuforums.org/showthread.php?t=1021484)

I just got a 9400GT Nvidia graphics card for Christmas and I can't get a resolution higher than 1024*768 even though my monitor supports 1600*1200. I am using a DVI to VGA converter for the monitor. I think I'm having the problem because it's not detecting the monitor probably due to the converter. Does anyone know how I can force 1600*1200 (i.e. editing xorg file). 

Here is my xorg conf

```
DefaultDepth    24
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Option        "TexturedVideoSync" "on"
    Driver    "nvidia"
    Option    "NoLogo"    "False"
EndSection
```Thanks for any help in advance and merry Christmas. :KS

---

### Post by northern lights on 2008-12-26
What Ubuntu release are you on?

Did you have an nvidia graphics device before also?

The question what release your on is important, as the Intrepid repositories offer four different nvidia drivers. The following goes for Intrepid:
Run```
sudo apt-get update && sudo apt-get install nvidia-glx-177 nvidia-xconfig nvidia-settings
```to install the driver and two essential packages for setting up your card, if either was already installed, the command will not alter anything.

After package installation, run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```and subsequently```
nvidia-xconfig
```
Thereupon pick your desired settings.

You should be done.

As an aside: Multiple threads on the same problem are generally no too advisable...

---

### Post by Jiffyman on 2008-12-27
I am currently running 8.10 using an Internet upgrade from 8.04. I installed the driver using the drivers manager. I tired your commands and this is what I got for the first one. 

```
geofferey@Ubuntu-X64-Desktop:~$ sudo apt-get install nvidia-glx-177 nvidia-xconfig nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-settings is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-xconfig: Conflicts: nvidia-glx
E: Broken packages
geofferey@Ubuntu-X64-Desktop:~$ 
```I uninstalled the driver before initiating these commands, if that helps any.

Edit: I reinstalled the drivers with the Hardware Drivers tool. Then issued the command:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```I now have the options to choose a higher resolution in NVIDIA X Server Settings, but when I choose a resolution higher than 1024*768 and click apply it says my monitor is out of scan range. The higher resolutions are not listed in Ubuntu's screen resolution properties however. Could it be because I am using a DVI to VGA converer?

---

### Post by northern lights on 2008-12-27
Didn't figure nvidia-glx-177 and nvidia-xconfig would conflict.

Anyhow nvidia-glx-177 is the driver you'd want. If you have it set now, driver's shouldn't be altered.

There shouldn't be a problem with DVI per se, but I have never used a converter.

Can you manually choose a different screen?

---

### Post by Jiffyman on 2008-12-27
> **northern lights said:**
> 
Can you manually choose a different screen?

I'm not quite sure what you mean. I did a reinstall of Ubuntu 8.10 with the cd instead of an update. I was using 64bit now I'm using 32.  Right now I'm applying all the updates then I will enable the driver again. Things started to go a little whacky on my install after I tried to install KDE 3 on it. I'll let you know how it goes.

---

### Post by redsoxreed on 2008-12-27
You might want to check this out: (it applies to Ubuntu as well)

[http://forums.debian.net/viewtopic.php?t=26577&highlight=x+modeline](http://forums.debian.net/viewtopic.php?t=26577&highlight=x+modeline)

---

### Post by Jiffyman on 2008-12-27
Well the reinstall fixed all my problems. Thanks for all of the help.

---

