---
title: "Desktop Effects could not be enabled (was working yesterday)"
date: 2010-01-21
forum: Desktop Environments
---

### Post by mbelos on 2010-01-21
Hey guys, when I try to enable 'normal' desktop effects, I get an error saying that the "Desktop effects could not be enabled". This was working fine yesterday... I realised that my computer updated xserver-xorg-core and xserver-common (in my /var/log/apt/term.log file, it quotes version 2:1.6.4-2ubuntu4.1 for both). Could this be the issue?

I have the latest NVIDIA drivers installed (190.53), running Twinview (everything is working fine at the moment). I'm using Ubuntu 9.10 (x64), and below is the output from compiz-check

```

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation Device 0a28 (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

Any way I can downgrade the two packages above to test that out? Really annoying, since this all worked 24 hours ago...

---

### Post by ephman on 2010-01-21
hi,

seem to be having the same problem.  updated x-org, and now "special effects" won't work.  running the same nvidia driver as you.  the only difference is that i'm not running twinview.  does anybody have any ideas?  i'm totally at a loss.

> Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G96 [GeForce 9650M GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size



thanks for the bandwidth,

ephman

---

### Post by mbelos on 2010-01-21
I tried to downgrade the packages using Synaptic, but it didn't quite help (although I only Logged Out rather than restarted my computer - I'll try that later tonight).

---

### Post by ephman on 2010-01-21
you'll probably need to restart.  my "break" didn't happen till i restarted.  if you could let me know how the restart worked out for you that'd be great!

thanks,

ephman

---

### Post by mbelos on 2010-01-21
The restart didn't quite make a difference - it seems like I have *some* of the desktop effects, but I can't tell for sure. I followed this article though and it helped (Gnome-Do doesn't complain anymore about the Docky theme):

[http://maketecheasier.com/gnome-do-docky-a-new-dock-on-the-block/2009/02/12](http://maketecheasier.com/gnome-do-docky-a-new-dock-on-the-block/2009/02/12)

Go down to where it says: "Turn on metacity compositing manager (only if Compiz does not work in your computer)" and follow the steps in the gconf-editor app

---

### Post by darco on 2010-01-22
Reinstall your drivers...always works for me.....

---

### Post by georgestan on 2010-01-22
Open Synaptic Package Manager, find the following packages

xserver-common
xserver-xorg-core
xserver-xorg-dev

Select Package->Force Version, and use the versions before upgrade.
Next, go to tty1 and stop the x server

Ctrl+Alt+F1 and then login, input

sudo /etc/init.d/gdm stop

and reinstall your proprietary driver.

Restart your computer and you are back again.

To prevent further upgrades on those packages before a solution comes out, use Lock Version feature in Synaptic manager.

---

### Post by BramWillemsen on 2010-01-22
I'm not sure if we had the same problem but i had something strange happening too this morning. Ubuntu could only boot into the low graphics mode after the updates of yesterday. the DRM modules could not be loaded by fglrx anymore (i use the ATI proprietary drivers). A reinstall of the ati drivers did the trick for me. I guess the latest updates messed something up for you too.

---

### Post by ephman on 2010-01-22
got it working... i uninstalled and then reinstalled the nvidia driver from their website, and all is now good!  did not have to force old versions of x-org.

thanks,

ephman

---

### Post by mbelos on 2010-01-22
Thanks for posting back - I'll give this a go later today. Did you use EnvyNG to uninstall the drivers?

---

### Post by rol7805 on 2010-01-23
Glad it's not just me. I just moved to Ubuntu from Windows and all was working fine for a few days til I rebooted today. I reinstalled the 190.53 driver but I don't think I ever "uninstalled" it. How do I do that?

---

### Post by ephman on 2010-01-24
> sudo nvidia-uninstall


or 

> sudo apt-get --purge remove $(dpkg -l | grep nvidia | awk '{print $2}')

should do the trick well.  good luck & glad you made the move from windows.  

ephman

---

### Post by Ian Clark on 2010-01-31
> **BramWillemsen said:**
> I'm not sure if we had the same problem but i had something strange happening too this morning. Ubuntu could only boot into the low graphics mode after the updates of yesterday. the DRM modules could not be loaded by fglrx anymore (i use the ATI proprietary drivers). A reinstall of the ati drivers did the trick for me. I guess the latest updates messed something up for you too.

Hey there. I was wondering how exactly you reinstalled your drivers. Is there a guide you used? Or was it simpler than that? I noticed in your comment that your situation is the same as mine. I had perfect functionality past a week ago, then suddenly this ATI card of mine is unsupported, no options listed etc. I'm wondering if it might effect video processing on my end.

I downloaded [this]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.25&lang=English") driver - but don't know what to do with it.

---

