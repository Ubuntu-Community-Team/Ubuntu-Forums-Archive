---
title: "Only blank desktop and cursor after installation"
date: 2013-06-19
forum: Desktop Environments
---

### Post by Dippmopser on 2013-06-19
Hello,

I just installed Ubuntu for the first time.

The installationprocess went smoothly as far as I can tell, however after booting for the first time and entering my credentials, I only see, what I guess is a blank desktop and a mouse-cursor.

I can move around the cursor and that's basically it.

I searched a little and found this thread:

[http://ubuntuforums.org/showthread.php?t=1499329](http://ubuntuforums.org/showthread.php?t=1499329)

I guess this is my problem as well. Since I am new to Linux, could someone please tell me, how I "add 'gnome-panel' and 'compiz' to the Startup menu [System->Preferences->Startup Applications] while in safe mode"?

I already figured out, how to enter safe mode (grub says recovery mode - I hope that is what I am looking for), thereafter I am presented with some options, those being:

resume Resume normal boot
clean Try to make free space
dpkg Repair broken packages
failsafeX Run in failsafe graphic mode
fsck Check all file systems
grub Update grub bootloader
networt Enable networking
root Drop to root shell prompt
system-summary System summary

A litte help what to to do from here on would be really nice.

Regards
Dippmopser

---

### Post by mjrich1976 on 2013-06-19
It's possible that you installed the *server* edition instead of the *desktop* edition. I made that mistake the first time I did it as well. Do you know specifically what you installed?

---

### Post by grahammechanical on 2013-06-20
What makes you think that that thread applies to your machine? How old is your hardware? When you say a "blank desktop," is there a background image? Can you right click the desktop? Do you see a menu? Select Change Desktop Background. That will open System Settings>Appearance. By the way, it is also helpful if you tell us what version of Ubuntu you are using. There is a new version every six months and they way things are done are being changed over time.

Assuming that you are using 13.04 (not my fault if you are not) once you open the Appearance Utility you can open the System Settings page and load Software & Updates utility. Go to the Additional Drivers tab and experiment with the video drivers listed there. You should wait a little while to let the utility search for appropriate video drivers. You may need to reboot.

For your information Recovery Mode>Resume will load Ubuntu without loading a proprietary video driver. If you are using 13.04 Resume will load an open source video driver for lower specification machines. You many find the performance less than ideal. I do not notice it too much. I am running the development branch and at the moment I sometimes need to use Recovery>Resume to get to a desktop. Once there you can load System Settings>Software & Updates>Additional Drivers tab and experiment with video drivers. And I do mean experiment. I have found the Nvidia drivers to not be up to standard lately.

Regards.

---

### Post by sinbowden on 2013-06-21
I know not my thread but same thing for me. also I cant do as u do and get same results. I have no video card drivers to play with like you?

---

### Post by oldfred on 2013-06-21
I sometimes get a blank screen with background.

I right click and it offers to change background. Then I go into the menu and system settings. From system settings I can get to Software & drivers and on the drivers tab install my nVidia driver. That I think is the long way around, most of the item I remember to use nomodeset on grub menu.
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by midnightramen on 2013-06-22
What I think you may be running into is that the opengl components may be disabled. You may want to download the 'CompizConfig Settings Manager' and use that to restore the defaults under Preferences within the 'CompizConfig Settings Manager'. You may be able to install using ```
sudo apt-get install compizconfig-settings-manager
```.

---

