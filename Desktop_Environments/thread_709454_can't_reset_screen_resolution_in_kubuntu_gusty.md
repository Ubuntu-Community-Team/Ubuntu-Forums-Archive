---
title: "can't reset screen resolution in kubuntu gusty"
date: 2008-02-27
forum: Desktop Environments
---

### Post by 7Aaron7 on 2008-02-27
hi,
when I try to reset (make lower) the resolution in administrator mode, nothing happens.  I went to the /etc/xorg config file, and there are 6 of them there!!

how can I get this to work?
thanks to all!!

---

### Post by OffAxis on 2008-02-27
Stupid question...Are you hitting the Apply button afterwards?

You can reduce the available options by running the 
```
sudo dpkg-reconfigure xserver-xorg
```

command.
It'll walk you through the xserver configuration for keyboard, mouse, monitor driver, and monitor. You can leave the current stuff intact by just pressing the Enter key to accept the current setting, and when you get to the 'Resolutions' section remove the asterisk (use the spacebar) from the available options, and you can eliminate options that you don't want to have or force a resolution by leaving only one asterisk there.
Just make sure that your monitor/video card support the resolution that you're trying to impose on it.

---

