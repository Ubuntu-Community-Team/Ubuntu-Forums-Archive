---
title: "Nvidia Driver?"
date: 2005-11-14
forum: Desktop Environments
---

### Post by chadwick359 on 2005-11-14
Hey there, I just installed Kubuntu on a 1.9 AMD machine with a Gforce 5500, and installed the nvidia drivers and nvidia-settings, setting the driver to "nvidia" in my xorg.conf file causes x to refuse to launch. if anybody could link to a nvidia driver howto for Kubuntu, or offer some troubleshooting, I would really appreciate it.

---

### Post by f1dave on 2005-11-14
Could you elaborate on how you installed your nvidia drivers? This would help me get an idea on what you might need to do, having installed them many times myself without too much trouble.

---

### Post by frodon on 2005-11-14
tseliot wrote a guide about latest nvidia drivers installation, it may help you : [http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia)

---

### Post by chadwick359 on 2005-11-14
I installed the nvidia-glx, the nvidia-kernel-common, and the nvidia-settings from adept. i then edited my xorg.conf and added the NVIDIA-Settings.desktop file. But every time i actually use "nvidia" as the driver entry for the device, x refuses to launch.

---

### Post by CAE on 2005-11-14
Why do people even bother editing their xorg.conf files manually? This is all you need to do:

```
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
```

And then restart X.

---

### Post by f1dave on 2005-11-14
Don't you need restricted kernel modules, too?

---

### Post by frodon on 2005-11-14
Yes you need it, but if you didn't change your kernel you should already have it. Besides if you installed your new kernel like that : [http://www.ubuntuforums.org/showthread.php?t=85917&highlight=kernel](http://www.ubuntuforums.org/showthread.php?t=85917&highlight=kernel) the restricted modules are installed too.

---

### Post by CAE on 2005-11-14
[QUOTE=f1dave]Don't you need restricted kernel modules, too?[/QUOTE]

Sorry, this is off-topic, but you and I have something in common - CS at UWA. ;)

---

### Post by chadwick359 on 2005-11-14
.

---

### Post by jdives on 2005-11-16
I reinstalled kubuntu, then installed the drivers before i did anything else.  For some reason this had an affect on things cause my 5500 is working now.

---

### Post by Takis on 2005-11-16
> **CAE]Sorry, this is off-topic, but you and I have something in common - CS at UWA.  said:**
> 
Bah, west-siders. Everyone knows the East side's where it's at.

On-topic: [QUOTE]installed the drivers before i did anything elseGood move. It's always a good idea to get all your hardware up and running before doing anything else.

---

