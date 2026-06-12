---
title: "Have I installed and started running graphics driver correctly?"
date: 2009-03-17
forum: General Help
---

### Post by stozi on 2009-03-17
I followed [this]("https://help.ubuntu.com/community/UniChrome") tutorial. I didn't know what "CD to directory meant," and I found no .run file, so I used thunar file manager, found the vinstall shell script, right clicked, and chose execute, then hit crtl-alt-bkspc. My xorg.conf looks like:

> 

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"dvorak"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection


Thanks!

---

### Post by circa82 on 2009-03-18
Your xorg.conf looks to be auto-configured -- doesn't say much.

Once you CTRL+ALT+BACKSPACE; you stop x and should be brought to a virtual terminal. Have you ran '[color=blue]startx[/color]' ? Results?

As for the instructions, say the downloaded file was called videodriver1.tar.gz and you downloaded it into your /home directory. You would open a terminal (Applications > Accessories > Terminal) and run the following:
```
# [color=blue]tar -xvf videodriver1.tar,gz[/color]
```
which will extract the contents of the tarball in it's own directory which will use the same name as the tarball only minus the .tar.gz
You then 'cd' into that new directory with:
```
# [color=blue]cd videodriver1[/color]
```
Inside the 'videodriver1' directory is where you'll find the 'run' file.
CD just means change directory (ie: cd <directory name>)

---

