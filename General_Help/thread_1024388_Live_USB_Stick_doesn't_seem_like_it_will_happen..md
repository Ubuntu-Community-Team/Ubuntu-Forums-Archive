---
title: "Live USB Stick doesn't seem like it will happen."
date: 2008-12-29
forum: General Help
---

### Post by smkoberg on 2008-12-29
Hey everybody,

I'm trying to put 8.10 on a Kingston Datatraveler 2GB USB drive and something isn't working. 

I'm using [this]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar") tutorial and I'm running into a few issues. 

First, when I get into fdisk I get the message about sector size, I should have made note of exactly when/where/what happened, but sadly I didn't. I found the tutorial in the [Ubuntu Wiki]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Making%20partitions") which pointed me to the [problem with 2GB USB drive]("http://syslinux.zytor.com/archives/2007-March/008284.html") post. Where I couldn't find an answer.

Secondly, after I ignored that first hiccup, when I got to section 3.3 Copying The Files To The USB Bar (in the original tutorial), I get an error that a few of the directories/files are missing.

Thirdly, I decided to try it all over again so I could find out exactly what fdisk was telling me when I ran commands, but when I try to delete/create new partitions, it doesn't seem to have an effect on anything. 

In short:
I'm running 8.04, trying to create a Live USB for 8.10, on a Kingston DataTraveler 2GB USB Thumb Drive, and it ain't working. :confused:

Any Thoughts?

---

### Post by john183 on 2008-12-29
use the builtin liveUSB creator (System>Administration>Create a USB startup disk) or use UNETBOOTIN. i have created six different LiveUSB disks with both of those programs. you just need to have an iso of the version of Ubuntu you want to use.

---

### Post by smkoberg on 2008-12-29
Don't have the Create USB startup disk option (using 8.04). Also, I don't have a regular Live CD with 8.10 on it, so I can't run the live CD, then create the Live USB. 

I tried UNETBOOTIN and it seemed to work, selected the distro, pointed it at the .iso file, and chose the USB drive. I ran into a problem when I tried to boot from the USB, it tells me that it's not bootable.

---

### Post by smkoberg on 2009-01-03
Created an actual Live CD, tried booting on my laptop, didnt work. Got a Buffer I/O error on device sr0 Logical block ....

Tried booting from the Live CD on my friends laptop, got into intrepid, then tried the built in USB Startup disk option, and it failed to create the bootable USB device.

---

