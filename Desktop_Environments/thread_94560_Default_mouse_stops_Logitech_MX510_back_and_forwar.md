---
title: "Default mouse stops Logitech MX510 back and forward buttons working"
date: 2005-11-24
forum: Desktop Environments
---

### Post by NiceGuy on 2005-11-24
Hi there, I've got an interesting quandary. I've got a Logitech MX510 mouse and set it up as per the instructions found on these wonderful forums - BUT there was a problem.

Everything worked except the back and forward 'thumb' buttons; well they worked but didn't go back and forward in firefox etc. (and yes the .xbindkeysrc file was set up correctly ;) )

I finally discovered that if I commented out the 'default' mouse bit in my xorg.conf file then low and behold, the back and forward buttons worked!

How ever I've now been left with a problem. From time to time I use a KVM switch which only supports ps/2 mice. I have a usb-ps/2 adapter but when I use this, ubuntu doesn't recognise my mouse and because I've commented out the 'default' mouse on my xorg.conf then the xorg doesn't launch etc.

Now as I see it there are two things I could do - Firstly I could setup my logitech mouse to work with PS/2 as well as USB (which might be good anyway so I could use the forward and back buttons when it is pluged into the kvm) or somehow get the 'default' mouse and logitech mouse bit of my xorg.conf to 'play nice', which would probably be better because if I ever wanted to use a 'normal' mouse, I could.

I suppose an ideal solution would be to do both!

The problem is I don't know how to do either of these things :( 

Any help anyone could give would be greatly appriciated!

PS. the relevant bit of my xorg.conf is shown below (with the 'default' mouse bit commented out)

```

#Section "InputDevice"
#	Identifier	"PS/2 Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ImPS/2"
#	Option		"Emulate3Buttons"	"true"
#	Option		"ZAxisMapping"		"4 5"
#EndSection

Section "InputDevice"
        Identifier	"Configured Mouse"
        Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB-PS/2 Optical Mouse"
	Option		"Dev Phys"		"usb-*/input0"
        Option		"Device"		"/dev/input/event2"
	Option		"Buttons"		"10"
	Option		"ZAxisMapping"		"4 5"
EndSection

```

---

### Post by NiceGuy on 2005-11-27
urm... bump :-({|=

---

