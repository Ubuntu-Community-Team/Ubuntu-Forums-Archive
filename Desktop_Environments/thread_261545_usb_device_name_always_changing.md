---
title: "usb device name always changing"
date: 2006-09-20
forum: Desktop Environments
---

### Post by richardq on 2006-09-20
I have a usb mouse and a Wacom Graphire3 tablet (also USB) attached to my machine. Upon reboot, I sometimes lose the Wacom functionality. It appears that the device name (ie. mouse3 or mouse2 or whatever) changes for the tablet each time. So I set it up for mouse3 once and next time my xorg.conf file needs to be edited to some other name (like mouse2).

Any ideas why this is happening?

---

### Post by kidders on 2006-09-20
I posted a vaguely similar thread a wee while back, and never got a response :-( :-( Boo hoo.

Basically, Linux handles device naming/numbering in a very fluid way. This has major advantages, but when you're trying to pin down a specific device with a config file like xorg.conf, it's a *real* pain.

Something you might want to look at is the contents of **/etc/udev/rules.d/**. These config files control the device naming schemes used by the kernel. I most often use it for simplistic stuff, like always ensuring my iPod is at /dev/ipod and won't jump around the place if I happen to plug a USB key in before it.

In theory, you should be able to construct udev rules to set the names of your input devices in stone, so X doesn't get confused. Input devices are a bit odd though, and like me, you may run into trouble :-(

I hope this is of some help! Feel free to post back if you need me to be more specific about anything.

---

