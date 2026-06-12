---
title: "Unity removed from ubuntu software center"
date: 2011-12-01
forum: Desktop Environments
---

### Post by pavi_elex on 2011-12-01
Can anybody please tell me, what will happen if I remove
Unity 2D,
Unity 2D panel,
Unity 2D places &
Unity 2D launcher
from ubuntu software center.
Please do not reply...... "Do & see".
I want real answer with explanation.

---

### Post by 3Miro on 2011-12-01
Originally nothing. You may run into a problem is say an update messes up your graphics driver, then you will not be able to login.

Why do you want to remove Unity 2D, it hardly takes any space on the HDD. Unity 2D only takes up RAM if you are actually logged into it.

---

### Post by 3rdalbum on 2011-12-01
> **pavi_elex said:**
> Can anybody please tell me, what will happen if I remove
Unity 2D,
Unity 2D panel,
Unity 2D places &
Unity 2D launcher
from ubuntu software center.
Please do not reply...... "Do & see".

Install Synaptic Package Manager. Tell it to mark those packages for removal. It will bring up a list of other packages it will remove as a result.

I don't think removing those packages would cause any immediate problems. If something goes wrong with your graphics driver, you won't have a 2D desktop to log into, so removing Unity 2D isn't such a hot idea.

If you remove other Unity packages such as libunity, you'll end off losing some of your programs.

---

### Post by grahammechanical on 2011-12-01
Is your hardware capable of running Ubuntu - Unity 3D? If the install of 11.10 put Ubuntu 2D as the default user interface and you remove Unity 2D without having installed some other user interface as a replacement then you could end up with a broken system.

Ubuntu 2D is the fall-back mode for when the installer detects a hardware setup that cannot run Ubuntu 3D. I think that if the hardware is capable of running 3D then 2D does not get installed.

I have had to install 2D in order to test it out. The people here are assuming that you have an alternative user interface that you can use. Your question is too general. If you remove those Unity modules using the Ubuntu Software Centre then they will be removed from the hard disk and you will not be able to log into the Unity 2D user interface.

Other than that, someone has to be the first to "do and see," otherwise they could not tell the rest of us what happens. I am confident that if I uninstalled 2D then my system will continue functioning because I am using 3D but I cannot say what will happen to your system.

Regards.

---

### Post by snowpine on 2011-12-01
Generally speaking, there is no reason to remove any of Ubuntu's default components, unless you are running very low on disk space.

---

### Post by kurt18947 on 2011-12-01
I had an experience that shows me why I don't want to uninstall Unity even though I very seldom use it.  I use gnome-shell 99% of the time but wanted to make some changes to printer defaults, e.g. print quality, default paper tray, that sort of thing.  I could not find a way to do that in gnome-shell.  In Unity it was quite simple primarily because Ubuntu has made Unity their primary focus and that's where the development resources go.

---

### Post by mc4man on 2011-12-01
If you're not using **unity-2d** then you can freely remove it. **Nothing** depends on unity-2d packages except other unity-2d packages

Ex.
> ~$ sudo apt-get purge unity-2d*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'unity-2d' for regex 'unity-2d*'
Note, selecting 'libunity-2d-private-dev' for regex 'unity-2d*'
Note, selecting 'libunity-2d-private0' for regex 'unity-2d*'
Note, selecting 'unity-2d-launcher' for regex 'unity-2d*'
Note, selecting 'unity-2d-panel' for regex 'unity-2d*'
Note, selecting 'unity-2d-places' for regex 'unity-2d*'
Note, selecting 'unity-2d-spread' for regex 'unity-2d*'
Note, selecting 'unity-2d-settings' for regex 'unity-2d*'
Package libunity-2d-private-dev is not installed, so not removed
The following packages will be REMOVED:
  libunity-2d-private0* unity-2d* unity-2d-launcher* unity-2d-panel* unity-2d-places* unity-2d-settings* unity-2d-spread*
0 upgraded, 0 newly installed, 7 to remove
After this operation, 4,035 kB disk space will be freed.

---

### Post by snowpine on 2011-12-01
4mb...

---

