---
title: "Where is xorg.conf in ubuntu 8.10??"
date: 2009-02-14
forum: General Help
---

### Post by jpaulb on 2009-02-14
I have a new install of Ubuntu 8.10 on an IBM A30 laptop, I have a problem that I have to hit the "'" key twice. Also ketboard config show the KB as 105 key international instead of 101. Usually this can be cured by changing a parameter in /etc/X11/xorg.conf however the is none in the folder.

Is X11 storing it's config file elsewhere now?

I tried sudo dpkg-reconfigure -plow xserver-xorg nothing is written to xorg.conf.

---

### Post by dcstar on 2009-02-14
> **jpaulb said:**
> I have a new install of Ubuntu 8.10 on an IBM A30 laptop, I have a problem that I have to hit the "'" key twice. Also ketboard config show the KB as 105 key international instead of 101. .........

System-Preferences-Keyboard-Layouts-Keyboard model.

---

### Post by SonnHalter on 2009-02-14
/etc/X11

---

### Post by jpaulb on 2009-02-16
> **SonnHalter said:**
> /etc/X11

From my original post
" /etc/X11/xorg.conf however there is none in the folder "

---

### Post by geraldm on 2009-02-16
You stated that you have to hit the " key twice as being a "problem"
The keyboard that you have selected is the international one, which is a 
layout that has "dead keys", and " is one of them.
The key is dead on the first keypress because the next key to be pressed determines which code is to be used.  You may need to do more research
on the dead keys, and the subsequent keypress to understand what codes
are provided with that keyboard type.  
[http://en.wikipedia.org/wiki/Keyboard_layout#Dead_key](http://en.wikipedia.org/wiki/Keyboard_layout#Dead_key)
Look in the section US-international
To get the " key to work on the first keypress, you would have to choose a 
layout that does that.  The US keyboard releases it on the first keypress.

This is a common misunderstanding of the US-International layout.  Perhaps
there should be some explanation or help provided to persons that select the
international layout.  Can you think of a way to make it clear that there are 
dead keys when the international layout is selected, and what those keys 
are? 

Gerald

---

### Post by jpaulb on 2009-02-17
Linux instructions if available are written for people who do not need them, it has always been that way.


Pre 8.10 if the XkbOptions" "lv3:ralt_switch in /etc/X11/xorg.conf is commented out, the keyboard will work as it should. 
That is what happens in Ubuntu 8.04 server installation.

However in 8.10 this can not be done since /etc/X11/xorg.conf is missing, like not there at all.

I have reinstalled Ubuntu 8.10 twice, once using their Windoze type installation boot.. and once using the boot  expert mode. In both cases  /etc/X11/xorg.conf is missing, not there at all.

You can run "sudo dpkg-reconfigure xserver-xorg" a /etc/X11/xorg.conf. file is created, however it is ignored by the system, even after a reboot. This was one of the first things I did.
With the second reinstallation I did not let the installation program auto search for the keyboard; just set it to us 101 keys, there is however no way to set it to the IBM A30 keyboard. 

Once the keyboard is set for international the gnome-keyboard-properties app can not change this to a non international

Anyway the bottom line is that if Ubuntu creates a configuration file for the x-server it has been moved to a location other than /etc/X11/.

---

### Post by eldragon on 2009-02-17
as of xorg 7.4, input devices are being hotplugged on the fly, this means everything is being handled by hal.

so, no matter if you had an xorg.conf file, your input settings would be ignored. if you wish to modify how your keyboard behaves, you have to set up a new policy file (or modify your existing one if there is one) to suit your needs.

im almost sure you can do that under system, preferences, keyboard, layout.
but dont quote me on that :D

find more about fdi files, its structure (xml), and allowed options and you will be dandy.

if you ask me, i liked the old xorg.conf file better. xml seems inhuman...

---

### Post by jpaulb on 2009-02-18
thanks eldragon

Now I know what happened to the config file.

It is as far as I know not possible to change the keyboard setting from 105 to a 101 kb. With a laptop I don't think unplugging it is an option I would like to investigate.:)

The xml is good for selling more books, I prefer not to spend my time reading and just hack the config file.

---

### Post by cdtech on 2009-02-18
> **Hardware Abstraction Layer:**

HAL provides an abstract view on hardware.

This abstraction layer is simply an interface that makes it possible to add support for new devices and new ways of connecting devices to the computer, without modifying every application that uses the device. It maintains a list of devices that currently exist, and can provide information about those upon request. ([http://packages.ubuntu.com/feisty/hal](http://packages.ubuntu.com/feisty/hal))
The xorg.conf file (/etc/X11/xorg.conf) still has the InputDevice for the mouse and keyboard, which are commented due to "input-hotplug" being used.
> The main idea behind keeping the discovery mechanism out of the server was that different systems can use different mechanisms. On GNOME or KDE desktops it would make good sense to use HAL for detection (which is a cross-platform device detection and enumeration system), but an embedded system may well want to use something more lean. ([http://www.x.org/wiki/XInputHotplug](http://www.x.org/wiki/XInputHotplug))
If you use these commented sections within the xorg.conf file (uncomment them) you would have duplicate devices. To use these you actually need to disable hal.

Keyboard and mouse configs can be writen to an .fdi file within the /etc/hal/fdi/policy/ directory. Here is a Ubuntu wiki page that explains the .fdi files: [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

Theres a lot of information about evdev, input-hotplug and hal but I thought I would give you some direction to start. In 8.04 and later a newer version of Xorg was implemented which now supports input-hotplug and now uses different keyboard and mouse configuration files.

Just more reading. Hope this helps...........

---

### Post by cmay on 2009-02-18
the xorg.conf is found on my intreid ibex where it should be. i did not do anything to update it or anything. 
[php]
out put of cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection[/php]

---

### Post by eldragon on 2009-02-18
> **cmay said:**
> the xorg.conf is found on my intreid ibex where it should be. i did not do anything to update it or anything. 
[php]
out put of cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection[/php]

this is probably the xorg.conf file coming from an upgrade. a clean install doesnt come with one as far as i know.

---

### Post by cmay on 2009-02-19
i just installed intrepid- i did install the kernel from ubuntu studio but other than that i did nothing. its not even fourteen days old this install. but it could be my ubuntu kernel has to do with it.

---

### Post by jocko on 2009-02-19
> **eldragon said:**
> this is probably the xorg.conf file coming from an upgrade. a clean install doesnt come with one as far as i know.
A clean install of intrepid *does* have an /etc/X11/xorg.conf (I have used both live and alternate cd's of both 32 bit and 64 bit intrepid, and they all made a xorg.conf file by default), but without any real settings in it.
If you add some settings they will override the automatically detected settings, so you can make it work just like before.
I'm not sure if xorg will accept any advanced keyboard config in xorg.conf, but the "´" key should be a dead key, for obvious reasons. Otherwise there would be no way of typing special characters like &#7811;, &#7809;, é, è, ý, &#7923;, ú, ù, í, ì, ó, ò, á, à, &#347;, &#501;, &#7729;, &#314;, &#378;, &#263;, &#324; or &#7743;, which are used in some languages. To get a single "´" you either press it twice or hit space after pressing it once (the key with "^", "~" and umlaut (äüïöëÿ) acts the same, for the same reason).

---

