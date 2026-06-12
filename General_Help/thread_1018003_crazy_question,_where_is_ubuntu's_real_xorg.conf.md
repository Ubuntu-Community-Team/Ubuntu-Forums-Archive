---
title: "crazy question, where is ubuntu's real xorg.conf ?"
date: 2008-12-21
forum: General Help
---

### Post by tjwoosta on 2008-12-21
i have installed quite a few distros before and they all have very complex xorg.conf's


i looked at my ubuntu 8.10 xorg.conf today and this is what i see

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

and thats it!!

thats my whole xorg.conf? wtf

where is the rest of it?

where are those devices configured?

right now everything is actually working fine and i dont actually have to edit my xorg.conf, im simply curious where all of the configurations are in ubuntu just so i can check them out and see how it compares to my arch xorg.conf and maybe see what i could do different

---

### Post by jimmy the saint on 2008-12-21
from what I understand xrander is being used for configuration.  I am not sure that that completely eliminates the impact of Xorg, but someone mentioned that editing Xorg is deprecated so I assume that many of the settings are now contolled via xrander as opposed to Xorg.conf

---

### Post by markbuntu on 2008-12-21
This is not an Ubuntu issue. It is an Xorg decision to move to automatic deault configuration and leave optional configuration to user space applications.

xorg.conf is being deprecated.

---

### Post by tjwoosta on 2008-12-21
so there is no way to view the configurations?

---

### Post by markbuntu on 2008-12-21
They are scattered about in system/preferences apps. if you are using proprietary drivers they have their own config apps.

---

