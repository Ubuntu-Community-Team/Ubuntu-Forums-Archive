---
title: "How to access USB drive using Sun Virtual Box"
date: 2009-11-29
forum: Desktop Environments
---

### Post by RSASKA on 2009-11-29
This thread is really a continuation of [http://ubuntuforums.org/showthread.php?t=1303859](http://ubuntuforums.org/showthread.php?t=1303859). I really appreciate everyone's help.

I poked around and figured how to get Sun Virtual Box ([http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)) to register my USB drive, and it finally works. Below are the steps it took on Ubuntu 9.04 and hopefully it help others.

After installing, and adding myself to vboxusers (for further clarification, see [http://ubuntuforums.org/showthread.php?t=1303859](http://ubuntuforums.org/showthread.php?t=1303859)), the next step would be to go to System -> Administration -> Users and Groups. A box labeled User Settings will appear. Select your username, click on Unlock and supply your password. Then, click on Propertiies, click on the tab User Privileges and check "Use VirtualBox." I also repeated the same process for root account.

Open Sun Virtual Box (Application -> System Tools -> Sun VirtualBox). Click on Details tab, scroll down to USB. Check "Enable USB Controller" and "Enable USB 2.0 (ECHI) Controller. Add new filter. (Please see attachment Add Empty Filter.png for clarification)

Start your virtual session, in my particular case it was Win XP. As soon as the virtual session is loaded, right click on the icon that looks like a USB stick, located on a lower-right corner of the window, and ensure the generic USB has been checked (please see attachment Ensure Generic USB is Checked.png). Every time you plug in a new device into USB port, go to the icon that looks like a USB stick, right-click to ensure that this plugged-in device is also checked.

---

