---
title: "How do you get windows borders?"
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by The Pinny Parlour on 2007-04-21
Uninstalled and installed both Compiz and Beryl and still can't get windows borders.  

How oh how do you get them to work?

---

### Post by The Pinny Parlour on 2007-04-21
Solved

---

### Post by Bundai on 2007-04-21
Can I ask how did you do this, might help other people, including myself.

---

### Post by The Pinny Parlour on 2007-04-21
I installed Beryl by downloading everything Beryl in Synaptic Package Manager.
I then added some code to my xorg.conf file by entering the following into Terminal:
```
sudo gedit /etc/X11/xorg.conf

```

I then copied   Option "AddARGBGLXVisuals" "True"   to the Section Device

So mine looks like this:
Section "Device"
	Identifier	"NVIDIA Corporation 7600GS"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option "AddARGBGLXVisuals" "True"

Once done close everything and hit Ctrl/Alt/Backspace to restart X

I then started Beryl by opening Applications/System Tools.  I'm now having fun with the settings.   Flames/fire and smoke on windows exit....cool.

---

### Post by Bundai on 2007-04-21
Hmm have to try this out.

---

