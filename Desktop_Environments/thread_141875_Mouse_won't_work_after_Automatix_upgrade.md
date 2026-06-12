---
title: "Mouse won't work after Automatix upgrade"
date: 2006-03-09
forum: Desktop Environments
---

### Post by xodeus on 2006-03-09
Hi all.
I've a small problem.
After I've runned Automatix my mouse won't work anymore.
I've tried to take the lines about Device Mouse from the backup xorg.conf file and replaced them in the running xorg.conf file but it still wont work...
Really don't know what to do. Here are the old ones:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

```
This worked for me...

Please help me.

---

### Post by Aine on 2006-03-09
I know it might seem silly, but have you tried to restart?

---

### Post by issueperson on 2006-03-09
automatix kept me from changing my applications menu.

i just uninstalled it and then it worked fine.

---

### Post by xodeus on 2006-03-10
Yes I've restarted my computer and I have uninstalled Automatix. It still does not work... I'll try with my other mouse...

---

### Post by dermotti on 2006-03-10
Make a backup of your xorg.conf


and run

sudo dpkg-reconfigure xserver-xorg


and see if that helps :-)

---

