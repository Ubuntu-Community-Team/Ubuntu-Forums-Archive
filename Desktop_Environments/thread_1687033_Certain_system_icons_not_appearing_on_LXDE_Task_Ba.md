---
title: "Certain system icons not appearing on LXDE Task Bar"
date: 2011-02-13
forum: Desktop Environments
---

### Post by epp on 2011-02-13
I have Ubuntu 10.04.2 LTS installed on an AMD K6-2 system, realizing that this is the last version of Ubuntu that will run on it, since they dropped support for non-CMOV processors.  :(

When logging in with LXDE, certain icons such as the HP Toolbox and the Update Manager do not appear on the LXDE Task Bar when they should.  The HP icon should appear after logging in (It automatically does with XFCE.)  For the HP icon to appear, I have to manually run HPLIP Toolbox.

The various Update Manager icons (gray - package manager working, orange - updates available, red - important updates available) also do not appear at all under LXDE automatically and the only way to see if there are any updates is to manually run Update Manager after a period of time, which should not be necessary.  These same icons also automatically appear under XFCE.

Is there something that I can look at to see why these are not appearing?  I know there is a file /etc/xdg/lxsession/LXDE/autostart but I'm not sure if that has anything to do with it.  Under "Desktop Session Settings", the only two items listed are Screensaver and PolicyKit Authorization Agent, neither of these are checked.

The only icons that appear automatically after an LXDE login, are the Network Connection, ScreenLock and Shutdown icons.

Both the -generic and -386 kernels are installed on this and it does not matter which kernel is selected at boot.

Thanks in advance for any suggestions.

---

### Post by cavalier911 on 2011-02-13
Same situation on Lubuntu 10.04.1 LTS

**_Anyone who knows:_**
Please post how to add HPtools and update-manager notification to system tray of lxpanel.
Thanks :KS

---

### Post by epp on 2011-02-13
Adding ```
hp-toolbox
``` to the end of the **/etc/xdg/lxsession/LXDE/autostart** file, will launch the HP Toolbox at an LXDE login, however ```
hp-toolbox
``` by itself, causes it to fully launch and open.  

I would like that to load so that it only shows the HP icon in the Taskbar, as it does with the other graphical desktops.

---

### Post by epp on 2011-02-26
No one knows?  :confused:

---

