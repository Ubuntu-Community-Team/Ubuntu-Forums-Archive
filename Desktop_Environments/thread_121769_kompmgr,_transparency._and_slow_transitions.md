---
title: "kompmgr, transparency. and slow transitions"
date: 2006-01-25
forum: Desktop Environments
---

### Post by Vetto on 2006-01-25
OK...I have an ATI Radeon Mobility 9000 and here is a section from my xorg.conf file:
```

ection "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option          "BackingStore"		"true"
    Option "AccelMethod" "exa"

EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection
```

In kcontrol -> Desktop -> Window Behavior, I have the "fade-in windows" checked and "fade between opacity changes" unchecked.  I also have shadows on.  The computer is working just fine with the following exceptions:

1.  Transitions between windows is agonizingly slow...CPU only hits 30-40% but transition takes upwards of 5 seconds or more.  Imaging this delay when an app throws an information pop-up...unbearable.

2. cant turn off shadows or the "fade-in windows" as a normal user...can do it if I "sudo kcontrol" but those settings dont seem to be active under my user (are these settings user specific?  and if so where can I co to edit the "text" file config version if there is one for these KDE settings.

---

### Post by Vetto on 2006-01-28
I think  I found the file....kwinrc
but the changes I made to that file dont seem to stay through a reboot...I like the transparancy for the inactive windows but this is too much of a hassle.  There should be no reason that the transitions are slow...I can play F.E.A.R. and other hight perfomance FPS's with no lag or problems...If it is this poor then it really shouldnt have been included in a release version of KDE.

---

