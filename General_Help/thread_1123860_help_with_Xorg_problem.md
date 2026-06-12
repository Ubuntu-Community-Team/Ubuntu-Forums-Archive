---
title: "help with Xorg problem"
date: 2009-04-12
forum: General Help
---

### Post by Universal344 on 2009-04-12
I installed a minimal ubuntu (command line only) in a virtual machine.  I ran sudo apt-get install xorg xdm icewm.  On reboot I get the xdm login screen but I cannot use the mouse or keyboard.  I have a feeling I need to configure something in Xorg to get them to work.  I remember reading that there may be problem with the mouse and keyboard when X is initiated by the user as the /dev directory is often restricted.  However, the problem persisted when I ran it from the recovery mode root terminal.  I appreciate any help you can provide.

---

### Post by zvacet on 2009-04-13
First backup your xorg.conf file

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```

then edit your xorg.conf from recovery mode

```
sudo nano /etc/X11/xorg.conf
```

and you should see lines 

#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#	Option		"XkbOptions"	"lv3:ralt_switch"
#EndSection

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

---

### Post by kerry_s on 2009-04-13
you need to install hal> **sudo apt-get install hal**

---

