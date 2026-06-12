---
title: "VGA (KVM switch) issue"
date: 2012-07-26
forum: Desktop Environments
---

### Post by kali999 on 2012-07-26
Hi,
I have problem with ubuntu 12.04, i'm testing some desktops using this platform and sometimes when i plug VGA connector from KVM switch Ubuntu don't recognize monitor and switching it off, on this same unit when i plug DVI everything is working correct. Do you can help me with this kind of issue ?

---

### Post by kali999 on 2012-08-07
Any ideas ?

---

### Post by kansasnoob on 2012-08-07
Maybe it's this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/988290](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/988290)

I'm Erick there. I'm pretty sure it's a 'gnome-screensaver' issue, at least AMSlider verified that switching to 'xscreensaver' worked for him also.

---

### Post by kali999 on 2012-08-07
Is there any possibility to change output signal from DVI to VGA ? I've tried to change/remove/disable screenserver but it doesn't helped.

---

### Post by papibe on 2012-08-07
Hi kali999.

My first guess is that the Monitor's EDID information is not passing through the KVM.

Depending on you graphic card, it might be possible to obtain the EDID into a file (while the monitor is directly connected), and then hardcode it in your X configuration file.

What graphic card do you have?

Regards.

---

### Post by kali999 on 2012-08-08
like i wrote i use it to test desktops, they are diffrent manufacturer so i can't specify what kind of card is, the most it's intel integrated card but not only.

---

### Post by kali999 on 2012-10-09
I've done this, problem is resolved after adding nomodeset to grub starting line, do anyone know why auto resolution have this issue ? :S

---

