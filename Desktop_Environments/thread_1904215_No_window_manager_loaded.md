---
title: "No window manager loaded"
date: 2012-01-04
forum: Desktop Environments
---

### Post by l07 on 2012-01-04
I was trying to see whether using a different video driver might be better, so I clicked to install one in Additional Drivers. They're named similarly, so I don't know which one is better. Anyway, upon rebooting it switched to pc input (used to be dvi) and now after the restart the screen was getting darker when it was busy or something, so I didn't like it and tried to switch to the other driver.

Now upon the last restart, gui login isn't there at all. I do see the splash screen though, but only the command line log in.

---

### Post by dazza5000 on 2012-01-04
I am having this same exact issue running 12.04. I did an upgrade and rebooted and now all I get is a small command prompt when the desktop environment appears to load.

---

### Post by wildmanne39 on 2012-01-04
Hi dazza5000 since you are using 12.04 developmental version for testing only you need to ask your question here please:
[http://ubuntuforums.org/forumdisplay.php?f=412](http://ubuntuforums.org/forumdisplay.php?f=412)
Thanks

---

### Post by wildmanne39 on 2012-01-04
Hi l07, you can have a look at this link it may allow you to boot so you can uninstall the driver and install the other one again.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by l07 on 2012-01-05
nomodeset didn't work, neither did fixing packages in recovery menu, and neither did using fail-safe graphics, which only displayed a message about graphics not working. If you can give me the command to install the proper driver, I can type it in.

---

### Post by wildmanne39 on 2012-01-05
Hi, we do not even know what video card you are using.

These commands should remove the xorg file and reconfigure the x server and allow you to boot.
```
sudo rm /etc/X11/xorg.conf
```
```
sudo dpkg-reconfigure xserver-xorg
```
Thanks

---

### Post by l07 on 2012-01-06
Thanks, that worked great. Why did it need to be reconfigured?

---

### Post by wildmanne39 on 2012-01-06
Hi, because you changed your driver and  ubuntu did not like it so we needed to get rid of the new xorg file it created when you installed the driver and start over.
Thanks

---

