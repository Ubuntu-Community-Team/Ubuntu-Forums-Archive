---
title: "Installing Nvidia crashes KDM"
date: 2008-01-04
forum: Desktop Environments
---

### Post by lazylogic on 2008-01-04
New to Kubuntu (7.10) and did an install. 

Everything is perfect !  until I tried to install Nvidia.


PC Specs  -  Core 2 Dual, 3GHz, Nvidia 7500

Installed Nvidia using several methods including :
1.System settings -> advance -> restricted drivers
2. Installing via adept -> nvidia-glx
3. Installing via adept -> nvidia-glx-new
4. Installing package downloaded from Nvidia
5. Install Nvidia by any of above 4 methods but replace xorg.conf with a copy of debian's working xorg.conf.

All methods resulted in KDM crash upon reboot, there is no gui to key in the userid and password to login.

CTRL-ALT-F1 allows me to go to console to restore the backup xorg.conf and a reboot will get me back to normal (without Nvidia off course).

The same pc runs Debian and openSUSE with Nvidia, without problems.

Any idea what is wrong here?

---

### Post by dreadlord_chris on 2008-01-04
it would be easier if I could see the actual error messages, but I suspect this has to do with conflicting drivers laying around on your system...

I'm using the NVIDIA 7300LE and stopped relying on Ubuntu's "officially" provided packages quite a while ago...

first thing, you need to go thru and uninstall _**all_** NVIDIA driver packages - make sure to purge not just remove...

Now you *should* be able to install the driver provided by NVIDIA - just make sure you stop X before trying to install, and when the installer asks if you should let it update your xorg.conf - Just Say No ;-)

edit your xorg.conf yourself and just change the driver from vesa (or whatever) to nvidia
Save
Restart X
```

sudo /etc/init.d/kdm start

```

does that help?

---

### Post by lazylogic on 2008-01-05
> **dreadlord_chris said:**
> it would be easier if I could see the actual error messages, but I suspect this has to do with conflicting drivers laying around on your system...

I'm using the NVIDIA 7300LE and stopped relying on Ubuntu's "officially" provided packages quite a while ago...

first thing, you need to go thru and uninstall _**all**_ NVIDIA driver packages - make sure to purge not just remove...

Now you *should* be able to install the driver provided by NVIDIA - just make sure you stop X before trying to install, and when the installer asks if you should let it update your xorg.conf - Just Say No ;-)

edit your xorg.conf yourself and just change the driver from vesa (or whatever) to nvidia
Save
Restart X
```

sudo /etc/init.d/kdm start

```does that help?

dreadlord_chris, you are sharp!

somehow the default installation of Kubuntu installs a nvidia package.
 did what you've advised and it works perfectly now, thanks!

---

### Post by dreadlord_chris on 2008-01-05
> **lazylogic said:**
> dreadlord_chris, you are sharp!

somehow the default installation of Kubuntu installs a nvidia package.
 did what you've advised and it works perfectly now, thanks!

My pleasure :KS

---

