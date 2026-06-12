---
title: "What options can I add to Xorg.conf with the Intel Driver?"
date: 2009-05-20
forum: General Help
---

### Post by asuastrophysics on 2009-05-20
hey all,

i'm suffering from slow framerates when playing videos online. the framerate isn't too bad since updating flash, but if i move the cursor or exit from fullscreen, there is an enormous lag.

what additional options can be added to Xorg.conf?
I'm running Jaunty 9.04 with a fresh install using the GM 965 chipset

here is my xorg:
```
Section "Device"
	Identifier	"Configured Video Device"
	Option 		"AccelMethod" "EXA"
	Option 		"ExaNoComposite" "false"
	Option 		"MigrationHeuristic" "greedy"
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

---

### Post by fillintheblanks on 2009-05-20
might want to have a look here [http://ubuntuforums.org/showthread.php?t=1136738&highlight=alternative+intel](http://ubuntuforums.org/showthread.php?t=1136738&highlight=alternative+intel)

---

