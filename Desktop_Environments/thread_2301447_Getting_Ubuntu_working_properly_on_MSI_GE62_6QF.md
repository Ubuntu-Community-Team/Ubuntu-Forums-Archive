---
title: "Getting Ubuntu working properly on MSI GE62 6QF"
date: 2015-11-02
forum: Desktop Environments
---

### Post by krzysiekcrpgfan on 2015-11-02
[COLOR=#111111][FONT=Ubuntu]I recently bought na laptop MSI GE62 6QF ([http://www.msi.com/product/notebook/GE62-6QF-Apache-Pro.html](http://www.msi.com/product/notebook/GE62-6QF-Apache-Pro.html)) with i7 6700 processor and NVIDIA GTX970M \ Intel 530 graphics.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have Windows 10 installed but it's just for games, I am generally Linux user, so wanted to install Ubuntu MATE 15.10 on second ssd hard drive. And here the story begins: first I could not even launch the live CD to install it, after some research I added "nomodeset" kernel option in GRUB and was able to sucessfuly install it. After installation I had to use "nomodeset" option to launch it, otherwise it just hangs. But with that option system is very laggy, windows are rendered forever (because nouveau driver id kind of disabled).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So I wanted to install nvidia drivers, first i installed 352 NVIDIA drivers from Additional Drivers menu. After installation and reboot system is very fast but drivers does not work properly:[/FONT][/COLOR]

[LIST=1]
[*]I could not get Compiz to work, I checked "glxinfo" command and here is the output:
[/LIST]
[INDENT]name of display: :0.0 Xlib: extension "GLX" missing on display ":0.0". Xlib: extension "GLX" missing on display ":0.0". Xlib: extension "GLX" missing on display ":0.0". Xlib: extension "GLX" missing on display ":0.0". Xlib: extension "GLX" missing on display ":0.0". Xlib: extension "GLX" missing on display ":0.0". Xlib: extension "GLX" missing on display ":0.0". Error: couldn't find RGB GLX visual or fbconfig Xlib: extension "GLX" missing on display ":0.0". Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0". Xlib: extension "GLX" missing on display ":0.0". Xlib: extension "GLX" missing on display ":0.0". Xlib: extension "GLX" missing on display ":0.0". Xlib: extension "GLX" missing on display ":0.0". Xlib: extension "GLX" missing on display ":0.0".
[/INDENT]

[LIST=1]
[*]The other thing is when I try to launch Nvidia Settings from command line I get:
[/LIST]
[INDENT]Xlib: extension "GLX" missing on display ":0.0". ** Message: PRIME: No offloading required. Abort ** Message: PRIME: is it supported? no
ERROR: nvidia-settings could not find the registry key file. This file should have been installed along with this driver at /usr/share/nvidia/nvidia-application-profiles-key-documentation. The application profiles will continue to work, but values cannot be prepopulated or validated, and will not be listed in the help text. Please see the README for possible values and descriptions. And there are just 2 options in window that is showed "Application profiles" and "nvidia-settings configuration"
[/INDENT]
[COLOR=#111111][FONT=Ubuntu]I tried everything:[/FONT][/COLOR]

[LIST]
[*]Installing newer 355 drivers using
[/LIST]
[INDENT]apt-get install nvidia-355 nvidia-prime
[/INDENT]

[LIST]
[*]Installing newer 4.3 RC7 kernel
[*]Installing bumblebee
[*]Trying nvidia-xconfig
[*]Modifing xorg configuration manually.
[*]Install other distrubution like Antergos - with similar issues.
[*]Adding i915.preliminary_hw_support=1 kernel option.
[/LIST]
[COLOR=#111111][FONT=Ubuntu]I have no idea to to proceed with that, My /var/log/Xorg.0.log file: [http://pastebin.com/e4wLaefT](http://pastebin.com/e4wLaefT)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Please let me know if you have any suggestions what should I check or do.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks in advance.[/FONT][/COLOR]

---

### Post by grahammechanical on 2015-11-02
Personally, if I was to install a release candidate kernel I would expect problems with proprietary video drivers.

It seems that Additional Drivers correctly installed Nvidia 352 driver but you say: "does not work properly." What were you expecting? You have hybrid graphics and the Nvidia Linux drivers do not do everything the Nvidia Windows drivers do. Were you expecting to get automatic switching from Intel graphics to Nvidia graphics and back again? I do not think that is possible on Linux.

What you are seeing with Nvidia Xserver settings

> there are just 2 options in window that is showed "Application profiles" and "nvidia-settings configuration"[COLOR=#111111][FONT=Ubuntu]I tried everything:[/FONT][/COLOR]

happens when we try installing an beta Nvidia driver on a release candidate kernel. The driver kernel module does not compile but the Nvidia Xserver utility installs anyway. I get that situation if I try to install the latest Nvidia driver on a standard kernel because the latest Nvidia drivers do not support my older Nvidia video card.

You have newer Nvidia hardware with the newer Linux kernels and the newer Nvidia drivers in 15.10 Additional Drivers. That is the best that Ubuntu has to offer at this moment. If we go outside that we must expect problems.

This is what others have found when testing the 4.3 release candidate 7 kernel

[http://ubuntuforums.org/showthread.php?t=2294800](http://ubuntuforums.org/showthread.php?t=2294800)

When I experimented with release candidate kernels and beta proprietary video drivers it messed up Additional drivers which would not let me change video drivers. I needed to purge the Nvidia driver and restart a couple of times before Additional Drivers got back to normal.

It has been some months since I installed Ubuntu Mate. I am unfamiliar with the method used by the Mate desktop to switch between Compiz as the compositor/window manager and whatever alternative Ubuntu Mate offers. But I guess we do need to switch. We cannot be using 2 windows managers at the same time.

Regards.

Edit: How to switch from Marco to Compiz in Ubuntu Mate; How to tell Compiz is working and what effect Compiz can give on Ubuntu Mate

[https://ubuntu-mate.org/blog/compiz-in-ubuntu-mate-vivid-vervet/](https://ubuntu-mate.org/blog/compiz-in-ubuntu-mate-vivid-vervet/)

---

### Post by krzysiekcrpgfan on 2015-11-02
> **grahammechanical said:**
> Personally, if I was to install a release candidate kernel I would expect problems with proprietary video drivers.

It seems that Additional Drivers correctly installed Nvidia 352 driver but you say: "does not work properly." What were you expecting? You have hybrid graphics and the Nvidia Linux drivers do not do everything the Nvidia Windows drivers do. Were you expecting to get automatic switching from Intel graphics to Nvidia graphics and back again? I do not think that is possible on Linux.

What you are seeing with Nvidia Xserver settings



happens when we try installing an beta Nvidia driver on a release candidate kernel. The driver kernel module does not compile but the Nvidia Xserver utility installs anyway. I get that situation if I try to install the latest Nvidia driver on a standard kernel because the latest Nvidia drivers do not support my older Nvidia video card.

You have newer Nvidia hardware with the newer Linux kernels and the newer Nvidia drivers in 15.10 Additional Drivers. That is the best that Ubuntu has to offer at this moment. If we go outside that we must expect problems.

This is what others have found when testing the 4.3 release candidate 7 kernel

[http://ubuntuforums.org/showthread.php?t=2294800](http://ubuntuforums.org/showthread.php?t=2294800)

When I experimented with release candidate kernels and beta proprietary video drivers it messed up Additional drivers which would not let me change video drivers. I needed to purge the Nvidia driver and restart a couple of times before Additional Drivers got back to normal.

It has been some months since I installed Ubuntu Mate. I am unfamiliar with the method used by the Mate desktop to switch between Compiz as the compositor/window manager and whatever alternative Ubuntu Mate offers. But I guess we do need to switch. We cannot be using 2 windows managers at the same time.

Regards.

Edit: How to switch from Marco to Compiz in Ubuntu Mate; How to tell Compiz is working and what effect Compiz can give on Ubuntu Mate

[https://ubuntu-mate.org/blog/compiz-in-ubuntu-mate-vivid-vervet/](https://ubuntu-mate.org/blog/compiz-in-ubuntu-mate-vivid-vervet/)
Thank you for the reply,

The reason I installed 4.3 kernel is to check if that solves the problem, with no success, I can go with 4.2 stable kernel. Effect is the same. I am not expecting for ubuntu to switch between graphics cards or any other advanced features, I would be happy if just Intel graphic card would work correctly. Generally I know how to use compiz, i used it before, It is simply a matter of choosing it in MATE settings, and it's available there without nvidia drivers installed, but system is very laggy and not usable (glxinfo shows proper results). I think it's laggy because of "nomodeset" kernel parameters, but without it ubuntu is not working at all. That's why I wanted to install nvidia drivers. But after installation glxinfo shows bad results, there is no openGL available and compiz (and possibly any other things that uses OpenGL are not available).

I used all that before on Dell laptop and there was no problems. This is probably related to 6th gen skylake processor or GTX970 graphics but not sure, that's why I posted here, maybe someone will know :)

Regards

---

