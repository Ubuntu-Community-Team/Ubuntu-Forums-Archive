---
title: "Mouse buttons in Opera"
date: 2006-06-05
forum: Desktop Environments
---

### Post by mejy on 2006-06-05
I use Gnome, and after playin with my xorg.conf and imwheelrc (imwheel obviously being installed), I now have my back and forwards thumb buttons working fine in gnome (nautilus, firefox and epiphany).  The mouse is a recent OEM logitech mouse (about 6 months old, came free with a moniter).

However, with qt apps (most importantly Opera), they seem to act something like the scrol wheel, although not exactly - they can collapse catergories in kcontrol.

Following are my imwheelrc and xorg.conf.

*/etc/X11/imwheel/imwheelrc*
```

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

```

*Relevant section of /etc/X11/xorg.conf*
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"11"
	Option		"ZAxisMapping"		"4 5"
EndSection

```


*And the script I use to get imwheel working:*
```
#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 8 9 4 5" &
exec imwheel -k -b "89" &
exec $REALSTARTUP

```

Any help much appreciated.

---

