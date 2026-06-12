---
title: "&quot;Distribution upgrade&quot; broke my X server"
date: 2007-03-08
forum: Desktop Environments
---

### Post by wilberfan on 2007-03-08
I just installed the "distribution upgrade" (?) for Edgy and my X server won't load now ("Failed to load NVIDIA kernel module")

This has to be a common problem, but I can't seem to find anything here about it...

---

### Post by taurus on 2007-03-08
Sounds like you have to reinstall nVidia driver again or modify /etc/X11/xorg.conf and replace **nvidia** with **nv** for the Driver.

```
sudo nano -Bw /etc/X11/xorg.conf
```

---

### Post by konungursvia on 2007-03-08
Taurus took the words right out of my mouth. Once you change that, hit ctrl-O to save and exit at the same time, then type startx to get going again. Then look up how to re-install your proprietary nvidia drivers, like through "envy".

---

### Post by wilberfan on 2007-03-08
That helped, thanks...   

Is there a compelling reason to re-install the nvidia drivers if I have no plans to install, for example, beryl?   :confused:

---

### Post by taurus on 2007-03-08
If you don't want to use 3D stuff (like Google Earth or something similar to that), then nv driver is good enough.

---

### Post by wilberfan on 2007-03-08
Ah.

Well I DO enjoy my google Earth from time to time, so that's good to know...   There must be threads about how to re-install nvidia?

Also, my ntfs-3g will not upgrade ("cannot authenticate package" or something like that...)   Is that related to the distribution upgrade, or a separate problem...?

Thanks for your ongoing help!

---

### Post by taurus on 2007-03-08
nVidia:
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by wilberfan on 2007-03-08
Damn, you guys are good...!   :)

---

### Post by wilberfan on 2007-03-08
Hey, it all went by so fast, I didn't even see what the distribution upgrade was all about...    Anyone happen to know what was upgraded, and why they call it a "distribution" upgrade?

---

### Post by wilberfan on 2007-03-08
Looks like this thread: [http://ubuntuforums.org/showthread.php?t=374125](http://ubuntuforums.org/showthread.php?t=374125) addresses the X server problem I was having (!)

---

### Post by wilberfan on 2007-03-08
As a note to myself, here's what helped:

First, download the latest (as of this writing) install script from NVIDIA:
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run)


Then do a ctrl-alt-F1 to get to a tty terminal.

login and do the following:

```
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

answer "No" when it asks if you want it to look for a "precompiled kernel interface"

I also answered "No" when it asked if I wanted my xorg.conf overwritten (!)

```
sudo /etc/init.d/gdm start
sudo reboot
```

Everything came up peachy!

---

### Post by konungursvia on 2007-03-08
Glad to hear it. But you should get beryl, it's so candy-ish.

---

### Post by wilberfan on 2007-03-08
> **konungursvia said:**
> Glad to hear it. But you should get beryl, it's so candy-ish.

Oh, I have a total chubby for beryl!   But I've never been able to get it running properly on Edgy.

I DID manage to get it up and running on openSuSE 10.2--even though it's a tad flaky for me...

Based on my experience there, maybe I'll give it another try on Edgy!  :guitar:

---

