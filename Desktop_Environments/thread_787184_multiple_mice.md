---
title: "multiple mice"
date: 2008-05-08
forum: Desktop Environments
---

### Post by Kirce on 2008-05-08
i have an MX 1000 mouse and i constatly forget to put it on the charge and it dies, so i have to wait for about 2 hours to keep doing what i was doing. 

On my windows machine i had 2 mice hooked up so if this happened i could just keep on truckin lol so i decided to try it and well much to my surprise it fails, i have my mx1000 hooked up thru usb and my other mouse (a genaric one) hooked up thru ps2 and well it dosnt like it, it has power and its lit up but it dosnt control the pointer.

Is there a way to fix this so they will both ontrol the pointer or a way i can swith between the 2 of them at any point?

---

### Post by Kirce on 2008-05-11
well i figured out the issue to get a secound mouse to work correctly you have to go to your /etc/X11 directory and edit the xorg.conf file so do this 

```

sudo gedit /etc/x11/xorg.conf

```

then type in your password and  find the section that has you're mouse should look like this

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

now once you have found it copy it and then past it below the current one, save, and close the file. 

you're secound mouse should work !!

---

### Post by mikeRimex on 2008-07-24
Check out [http://wearables.unisa.edu.au/mpx/?q=mpx](http://wearables.unisa.edu.au/mpx/?q=mpx)

---

