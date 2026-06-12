---
title: "xorg.conf resets after reboot"
date: 2009-05-08
forum: General Help
---

### Post by rob444 on 2009-05-08
Hello all, I recently managed to install the latest Nvidia drivers and it worked great. However... when I turned on the computer later I noticed that the Nvidia drivers are not being used anymore. So I ran "sudo nvidia-xconfig" and it mentions that some stuff are missing in xorg.conf, so it corrects it and makes a backup of old xorg.conf and sucessfully saves xorg.conf. I've even double checked this by viewing xorg.conf with gedit.

Now, if I reboot my computer, xorg.conf will have magically reset to the old xorg.conf with a lot of useful nvidia information gone to waste.

If I browse to /etc/X11 folder I see that there are several xorg.conf files, eg: xorg.conf.20090508203251. If I open any of these I can see that these are the modified xorg files that are being reset - that I want X to use!!!!

I'm fairly new to the linux system so bare with me, but I just don't get it why the xorg.conf file is being replaced each time I reboot.

As it is now I have to run sudo nvidia-xconfig and then do a sudo /etc/init.d/gdm restart and my Nvidia drivers will load properly, but it's not persistent...

Help :/

---

### Post by Alterax on 2009-05-08
Xorg is trying to reconfigure because something in the (working) files isn't working when the computer reboots.

I'm willing to bet that the particular NVidia driver that you're using isn't being loaded when the system starts up.  We can fix that, but to make sure, could you post the device section of one of those xorg files?  Then I can look up which driver needs to be added to the /etc/modules file.

Then, when the system reboots, the proper driver will be loaded into memory and X will be able to load properly--without needing to reconfigure itself.

---

### Post by rob444 on 2009-05-08
Hello! Thank you for taking your time to help me.

This is the device section nvidia-xconfig creates:

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection
```

And this is the device section nvidia-settings create if I save the settings through there:
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500M GS"
EndSection
```

I hope that will help you :).

---

