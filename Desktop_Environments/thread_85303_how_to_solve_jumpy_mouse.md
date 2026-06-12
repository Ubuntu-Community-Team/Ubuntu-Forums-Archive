---
title: "how to solve jumpy mouse"
date: 2005-11-02
forum: Desktop Environments
---

### Post by teaker1s on 2005-11-02
my mouse jumped occasionally and in my case I have a wireless 800dpi mouse so I 
sudo gedit  /etc/X11/xorg.conf and added the correct resolution for my mouse and it  now doesn't randomly jump or go slow
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
	**Option "Resolution" "800"**
EndSection

---

