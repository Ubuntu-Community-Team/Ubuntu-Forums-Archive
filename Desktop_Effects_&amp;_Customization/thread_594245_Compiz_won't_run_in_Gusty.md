---
title: "Compiz won't run in Gusty"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by Yes on 2007-10-27
I just did a clean install of Gusty, and when I try and start compiz, I get this:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4150 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "switch_windows"
```

My card is an ATI Radeon 9600.

---

### Post by avik on 2007-10-27
Did you install the proper drivers?  Try the Restricted Drivers Manager.

---

### Post by Yes on 2007-10-27
The restricted drivers made it so when GDM started, my screen went blank.  Where would I get the other drivers/how would I find out if I already have them?

Thanks.

---

### Post by skompier on 2007-10-27
I have the same card and did the following to get it working when I was running Gutsy.

First, run

```
sudo gedit /etc/X11/xorg.conf
```

Put 1 instead of 0 in the last section so it looks like this:

```
EndSection
Section "Extensions"
Option "Composite" "1"
EndSection
```


Then try again.. if it doesn't work... then do:
```

sudo apt-get install xserver-xgl
```

Restart X by doing cntr-alt-backspace

---

### Post by Yes on 2007-10-27
The extensions section crashed the X server and the xgl drivers were slow and buggy.  Thanks anyway.

---

### Post by avik on 2007-10-28
Try [Envy]("http://www.albertomilone.com/nvidia_scripts1.html").

---

### Post by Yes on 2007-10-28
I installed the drivers from Envy, and I still get the same errors.

---

