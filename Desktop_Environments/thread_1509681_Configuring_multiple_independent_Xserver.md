---
title: "Configuring multiple independent Xserver"
date: 2010-06-14
forum: Desktop Environments
---

### Post by Phyr on 2010-06-14
Hello everyone,
I have a computer, that I want to be accessible by more than one person at a time. At the moment I'm trying to configure it for two persons, but with the possibility to add more.
The computer has two video cards (oneboard/pci-express) with a monitor at each of them and two keyboards and mice and lastly an active usb-hub.
The Xservers are assigned one of each (one of the Xservers gets all the devices plugged into the usb-hub - at least it's planned that way). As gdm2 doesn't seem to support two Xservers anymore, I reverted back to xdm. Both Xservers have seperate configuration files so that I can specify the input devices in the InputClass section of the xorg.conf and typing/using the mouse only works in the Xservers it is meant to be.
Problems arise with removable media. I use gnome and when plugging in the media, it gets automounted for the user logged in at the latest started Xserver. The user at the other one gets an error message stating that the operation is "Not authorized". I took a look at dbus and the policykit, but it seems that I have to write my own script and start it via udev, as policykit seems not to be able to distinguish properly between the 2 sessions on the Xservers. The script would just automount all devices plugged in specific usb-ports (the usb-hub) for one user and the rest of the usb-ports for the other and if nobody is logged in at the associated Xserver then nothing happens until somebody logs in.
I'd like to know if you have some better ideas on how to get this working.
Is there maybe a way of getting policykit to understand the situation?
Is gdm2 really unable or did i miss something?
Thanks,
Phyr

---

