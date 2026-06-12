---
title: "HELP! Beryl on ATI Radeon 9600 in Feisty"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by LukeCarrier on 2007-08-28
Hello everyone,

I've been using Ubuntu full on for a couple of months, and so far it's been the best operating system I've ever used, and that includes Windows Vista that I'm currently dual booting.

Today I've installed Beryl using this guide:
[https://help.ubuntu.com/community/BerylOnFeisty](https://help.ubuntu.com/community/BerylOnFeisty)

All was going well until I launched the application in terminal via the command:
beryl-manager

Beryl loaded and attempted to change the window manager from Metacity to Beryl. The display flickered for a bit, but then returned to the Metacity window manager. The terminal window displayed this text:
luke@luke-desktop:~$ beryl-manager
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

As you can see, I'm using the ATI Accelerated Graphics Driver, as opposed the one Ubuntu ships with. I'm also using all the latest updates, which have caused no problems.

I've got these packages installed:
 - beryl
 - beryl-core
 - beryl-manager
 - beryl-plugins
 - beryl-plugins-data
 - beryl-plugins-unsupported
 - beryl-plugins-unsupported-data
 - bery-settings
 - beryl-settings-bindings
 - beryl-settings-simple
 - beryl-ubuntu
 - emerald
 - emerald-themes
 - heliodor
and all of the dependences Synaptic warned me about when installing them.

I did edit the configuration file for the xserver, but then set it back to its defaults when things didn't go the way I thought. I changed the area at the bottom that looks like:
Section "Extensions"
    Option        "Composite"    "0"
EndSection
To:
Section "Extensions"
    Option        "Composite"    "Enable"
EndSection
The error in the terminal then changed, I can't remember what to, but I can find out if you wish.

Please help me!
Luke Carrier

---

