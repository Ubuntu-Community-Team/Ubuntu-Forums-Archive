---
title: "Resolution in GDM is to high!"
date: 2007-05-11
forum: Desktop Environments
---

### Post by Xecuter on 2007-05-11
How can I change the screen resolution, and refresh rate, in GDM. My monitor only supports 1280x1024 and about 75Hz refresh rate (I think).

Where can I change this? I've looked in xorg.conf, but there are no numbers higher than 1280x1024.

---

### Post by zvacet on 2007-05-11
If your monitor supports 1280x1024,why do you want to set higher resolution?

[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

### Post by jjmatt on 2007-05-11
I'm pretty sure xorg supports higher than that. i'm currently running 1600X1200..
try this

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by RedSquirrel on 2007-05-11
[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?p=454217")

---

### Post by Xecuter on 2007-05-12
> **zvacet said:**
> If your monitor supports 1280x1024,why do you want to set higher resolution?

[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

I never said I wanted it higher. It is too high. I want to set it down.


>  HOWTO: change resolution/refresh rate in Xorg
Thanks, I'll try that. Do I have to reinstall the ATI drivers again after that?

---

### Post by RedSquirrel on 2007-05-12
> **Xecuter said:**
> Thanks, I'll try that. Do I have to reinstall the ATI drivers again after that?


I don't think so. As long as you have the correct driver for your video card, you can use that HOWTO to setup everything correctly in xorg.conf. For example, using a Modeline will allow you to use a specific refresh rate if the default configuration in xorg.conf didn't use the refresh rate (and/or resolution) you wanted. Just make sure you know what refresh rates your monitor can support, since using the wrong one is _bad_. ;)

---

