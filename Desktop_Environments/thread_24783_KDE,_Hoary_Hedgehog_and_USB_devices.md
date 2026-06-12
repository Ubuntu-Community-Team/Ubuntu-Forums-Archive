---
title: "KDE, Hoary Hedgehog and USB devices"
date: 2005-04-08
forum: Desktop Environments
---

### Post by rbowen on 2005-04-08
Greetings All,

I am pretty new to linux/kubuntu/kde but very impressed by the live and install releases of Hoary Hedgehog. After a lot of hacking about and thanks largely to various How To's and Fora and the web managed to get the Belkin F5D6001 wireless card to talk to the internet (Many thanks to all).

Recently, I was trying to get the USB pen interfaced and am somewhat confused.

I am using a USB mouse and that can be inserted and removed at will with no intervention on my behalf (other than plugging or un-plugging it)

When the USB pen is plugged in, dmesg shows that the device is recognised and correctly identifes the supplier of the device (Buffalo).

The devices shown by KDE are correct and in step with the state of pluggedness of the pen.

The device can be mount'ed using something akin to
mkdir /pen /* create mountnpoint */
followed by
mount -t vfat /dev/sda1 /pen -o nosuid,rw

The contents of /pen can be retrived using ls -al /pen, in the usual way.
Files can be created on /pen, etc. and even appear when the pen is plugged inti a WinXP machine

When I try to create a New device from KDE, thinking this was the right sort of thing to do, there are a number of options presented (hard disk, cdrom, zip drive, MO device). Having selected the device type, and chosen or entered a device (/dev/sda1), when I click "mount" an error message is presented (device xyz not found in /etc/fstab or /etc/mnt) but an icon is created on the desk top. When the icon is clicked, much the same thing happens.

Really there are two questions:
1) What should happen when a device is plugged into a USB port?
2) What connects the KDE options to the devices and howm is it configured.

Clearly, the hotplug/hotswap code in the kernel is behaving itself but equally I am missing something.

Can anyone point me in the right direction?

Many thanks for reading this screed. Any advice and guidance welcome

Yours Sincerley
Roger Bowen

---

### Post by nad on 2005-04-08
You have yet to add an entry in the file system table (/etc/fstab) for this device.

Not having used kubuntu, I can't give you the gui procedure. Just edit the captioned file to include your new device. Reviewing the existing entries should be all you need. If you would like more info about fstab, from the command line 'man fstab' or look in the help tab.

Good luck

Dan M

---

### Post by rbowen on 2005-04-08
[QUOTE=nad]You have yet to add an entry in the file system table (/etc/fstab) for this device.

Not having used kubuntu, I can't give you the gui procedure. Just edit the captioned file to include your new device. Reviewing the existing entries should be all you need. If you would like more info about fstab, from the command line 'man fstab' or look in the help tab.

Good luck

Dan M[/QUOTE]
 Many thanks for the reply. I'll give it a whirl

RB

---

### Post by rbowen on 2005-04-08
Greetings Nad

Many thanks for the tip.
a) it worked well enough
b) I can now understand why Konstantin Riabitsev wrote his script for "USB storage hotplug code" (https//listman.redhat.com/archives/rhl-devel-list/2003-August/msg00115.html)

Regards
Roger Bowen

---

