---
title: "kmilo functionality (IBM Thinkpad sound)?"
date: 2006-01-16
forum: Desktop Environments
---

### Post by thesnowysoviet on 2006-01-16
The last time I set up kmilo, it was on my Gentoo system.  For those who don't know, kmilo is hardware support for the volume and brightness buttons on IBM's Thinkpad series.  Unless kmilo is installed, these keyboard-extraneous buttons are of no use.

Adept seems to think that kmilo is installed and up-to-date; however, when I press one of the volume buttons nothing happens... no pop-up, no volume adjustment, nothing.

Any clues as to why kmilo doesn't appear to work?

---

### Post by MartinJ on 2006-01-17
I'm fairly sure that I didn't have to install the kmilo plugin to get the volume and thinkpad buttons to work, although I am using the plugin.  Can't quite remember what I did but it involved adding nvram to the list of modules loaded at startup and adding myself to the nvram group, or something like that.  

There's some [discussion in this thread]("http://www.ubuntuforums.org/showthread.php?t=81622").

---

### Post by wincen on 2006-10-21
[http://www.tuxme.com/node/544/1082]("http://www.tuxme.com/node/544/1082")

to sum up that link

> If you're using KDE(Kubuntu), there's really not much you need to do. By default, the ibm-acpi module should be loaded (check the output of lsmod) -- this will enable all of the hotkeys and function buttons (including volume and brightness).

KDE has two nice features that make life good for Thinkpad users: the kmilo service that will handle the volume/brightness keys (with a nice OSD for the same; and the IBM Thinkpad kcontrol module which lets you bind programs to various Thinkpad keys (like the Access IBM key). However, to make best use of both of these, we need to do some tweaking.

    * First, create a new group called nvram:

      sudo addgroup nvram
                          

    * Then add yourself to this group:

      sudo adduser [username] nvram
                          

    * Make sure that the nvram module gets loaded automatically on boot. Add nvram to /etc/modules on a new line.
    * Finally make sure that udev gives read/write permissions for the /dev/nvram device to all members of the nvram group. Make sure your /etc/udev/permissions.d/udev.permissions has the following lines:

      misc/nvram:root:nvram:660
      nvram:root:nvram:660
                          

    * Thats it! Next time you boot and log in, you should see nice OSD display when you press the volume or brightness or thinkpad light keys. And you should be able to bind the programs for the rest of the keys in the KDE control center. 


I'm using Dapper Drake and I did not need to do the step editting /etc/udev/permissions.d/udev.permissions.  I don't even have that file or the directory permissions.d

This worked for my T43

---

