---
title: "Gnome device icons"
date: 2009-01-02
forum: Desktop Environments
---

### Post by Sin@Sin-Sacrifice on 2009-01-02
So... why do all of my devices get defaulted to the drive-removable-media.png icon? I would like my PC to see the sd card icon that came defaultly when I slip one into the card reader. Same with usb drive and my cell phone. Any way to get gnome to look at the right icons for specific devices?

---

### Post by cdtech on 2009-01-02
Change your theme or right click on the icon goto properties and click on the icon to change it.

---

### Post by Sin@Sin-Sacrifice on 2009-01-02
I want the icon to change per the device not the usb drive. I changed one of the icons for my 1GB usb flash drive. Then unmounted it and put it in a different port it kept the icon. Leaving that in the same port I plugged in my G1 and and it stole the icon in stead of going to the phone icon in the .icons folder set aside for it. I would like the PC to react to the different devices and place the correct icon for that device. Is that possible without putting the device in the same port every time?

---

### Post by Sin@Sin-Sacrifice on 2009-04-26
Bump... old post but still interested.

---

### Post by darius.k on 2009-06-13
I'd be interested in a solution for this as well.
I mean it works for iPods I find it hard to imagine that you can't do the same thing for other devices. Is there not some place where we can associate specific icons to specific devices?

---

### Post by Sin@Sin-Sacrifice on 2009-11-18
I have since found a work around for this. Each device needs to be set a folder in /media or wherever you mount your drives and set to mount only to that folder in /etc/fstab. Then you can change the icon when the drive is mounted. Therein every time you mount that uuid it will bring up the icon.

---

