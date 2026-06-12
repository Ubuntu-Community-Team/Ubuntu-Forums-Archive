---
title: "USB Ports not working correctly"
date: 2009-04-24
forum: General Help
---

### Post by Rickje on 2009-04-24
Howdy all,

I got some issues with the last Sun Virtualbox (2.2) on Ubuntu w/ Gnome.
This is my current kernel:

> rick@Ubuntu:~$ uname -a
Linux Ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
Currently got a Windows XP virtualization running as you can see in the screenshot, I connect the Apple iPhone device and try to enable it within the USB Devices, but as you can see* from the screenshot *those usb devices can't be selected.

Is there anything I need to configure before Virtualbox would let me select my Apple iPhone from the USB Devices

I included a screenshot, hope somebody could help me.

-

---

### Post by Rickje on 2009-04-24
[FONT=Verdana]Sorry. I totally forget to mount my usb devices.

For others that have the same issue (Or with other usb devices) follow this:

Open a terminal and type this:
[/FONT][FONT=Verdana]grep vboxusers /etc/group

Then;

nano /etc/fstab

And add this line:

#Sun VirtualBox (2.2) usb mount (BUSGID) #Rickje <ubuntuforums.org>
none /proc/bus/usb usbfs auto,busgid=108,busmode=0775,devgid=108,devmode=0664 0 0

Change the busgid to the 'grep' command result that has been given.

Good luck.
[/FONT]

---

