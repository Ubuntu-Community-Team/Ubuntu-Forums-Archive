---
title: "X Server / gde hangs system when stopped"
date: 2007-03-16
forum: Desktop Environments
---

### Post by obscured on 2007-03-16
I've got a new machine put together recently, and I'm trying to get ubuntu up and running. I'm using Edgy atm. It took a bit as I was hung up by the fact that I have a nvidia 8800GTS, so I used the [workaround here]("http://www.ubuntuforums.org/showthread.php?t=379807") to force the vesa driver to load instead, and installed. Very fast and pleasant install from that point, I should say.

However, once installed, I go and download the drivers, and I'm trying to exit X to install the drivers. Any combination of ctrl+alt+bksp, ctrl+alt+f2, or /etc/init.d/gdm stop will have the screen go black, and then beep at me, and maybe beep again, and it hangs. nothing after that. 

Any ideas?

---

### Post by errhec on 2007-03-17
Since is this problem after you install the drivers for your graphic card, the problem would be in the drivers.
You should go in GRUB when loading and chose the safe mode.
After the comp is up you shoul type

sudo dpkg-reconfig xserver-xorg

and chose vesa, then try reinstall the drivers ( you should try envy) :)

Hope it helps
Err

---

### Post by obscured on 2007-03-18
No, I hadn't installed the drivers yet. I was **trying** to install them. I was still using vesa drivers at the time.

I did a work around by disabling gdm and installing before X started up, but that's not solving the problem, just avoiding it :) X seems to shut down just fine now with the proprietary drivers.

Envy? what's that? ok I'll go investigate :) thanks.

---

