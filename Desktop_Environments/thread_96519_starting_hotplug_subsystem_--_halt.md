---
title: "starting hotplug subsystem -- halt"
date: 2005-11-29
forum: Desktop Environments
---

### Post by shanz on 2005-11-29
I have a new sony vaio desktop with xp and media center edition pre-installed.

I intalled 5.10 with no problem.

But the boot up halt at "starting hotplug subsystem..."

Any help?
Thanks.

---

### Post by Ampersand on 2005-11-29
Try removing any pcmcia/usb devices and try again.

---

### Post by thedstro on 2005-12-02
I had the same problem! In my case disabling the on-board sound through the BIOS setup fixed it and allowed me to boot. This is just a workaround of course! The solution could be replacing the sound driver (intel_snd_hda I think it was called in my case) or changing to udev instead of hotplug.

---

### Post by Paloseco on 2005-12-09
anyway that module is not working properly for me, i have no sound.

---

### Post by fonkypij on 2005-12-09
Hi,

Try to download the HD audio install pack on the Intel's website. It provides you a sh installation script of the last Alsa (driver, libs and utils). 

Of course, Advanced Linux Sound Arch support must be enabled in your kernel configuration as a module.

---

