---
title: "How to get rid of Trackpad Clicking?"
date: 2005-12-10
forum: Desktop Environments
---

### Post by Plastic9mm on 2005-12-10
Hello all, I am a complete newbie here, so please bare with me.

I recently (last night) installed Ubuntu Linux (the first time I've ever tried any distro of Linux) on an old Sony Vaio PIII 800Mhz Laptop.

The installation went smooth and for the most part, I'm quite impressed with the system (doesnt hurt that its free too!). But I do have one issue that is really bugging the hell out of me...

The trackpad on the laptop has the ability for "Tap-clicking" ie: you tap on the trackpad, and it registers this action as a mouse click.

It is EXTREMELY ANNOYING, and I haven't found a way to disable it.  I checked the mouse preferences, but didnt see anything about the trackpad clicking... or how to disable it.  Can anyone out there please help me?

Thanks.

-9mm (ouT)

---

### Post by Plastic9mm on 2005-12-12
Ok so no one replied, but that's OK.

I finally figured it out with enough searching and trial an error testing.

So I'll post it here for others to find incase this can help them too. 

First, I thought i had a synaptics touchpad, I'm a complete newb to linux and i figured the OS would pick the right driver when detecting hardware anyways... pshhhh!

Turns out I'm using an ALPS touchpad... To figure out what kind of touchpad you are using, run this in the terminal: 

cat /proc/bus/input/devices

This should report back some hardware handlers, search and ye shall find the touchpad handler, mine looks like this:

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse1 event2 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

So next, I deciphered from various searches, that the xorg.config file was the next important peice... The file is located in /etc/X11/xorg.conf

The identifier here was completely inaccurate...

It read (past tense):

Section "InputDevice"
	Identifier	"SynapticsTrackpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/event2"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"

EndSection

This is where the handler id had to change for me to properly be able to configure my ALPS trackpad...

*note* to edit your xorg.conf file, make sure you have backed it up, and run "sudo gedit /etc/X11/xorg.conf" in the terminal. After editing the text that appears, click save.

Through another handful of searches i realized i had to Change the Identifier to "ALPS".  

I did not have to change the driver from "synaptics".

I also had to change the "Protocol" option to "event"

This is what the editted section looked like:

"InputDevice"
	Identifier	"ALPS"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/event2"
	Option		"Protocol"		"event"
	Option		"HorizScrollDelta"	"0"
EndSection

Now I resatrted, and well... it changed a bit I guess...

I searched a bit further and found out the command list for the driver (If I didnt have control now, fine. I'll get it the hardway), it is located at "/usr/share/doc/xorg-driver-synaptics/README.gz"

After a few restarts (my trail and error until i realized a whopping mistake!), my trackpad works nicely and I have advanced just a tinsy step further in my linux knowledge (lack of).

This is what the editted section of my xorg.conf looks like:

Section "InputDevice"
	Identifier	"ALPS"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/event2"
	Option		"Protocol"		"event"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"		"0"
	Option		"TapButton1"		"0"
	Option		"TapButton2"		"0"
	Option		"TapButton3"		"0"
	Option		"MaxTapMove"		"0"
	Option		"MaxDoubleTapTime"	"0"
	Option		"ClickTime"		"0"
	Option		"MinSpeed"		"0.5"
	Option		"MaxSpeed"		"0.5"
	Option		"AccelFactor"		"0"
EndSection

Now my trackpad is working beautifully, and everything is much more enjoyable.

-9mm (ouT)

---

### Post by Plastic9mm on 2005-12-12
GASP!

Whats that? YES I DID FORGET THE MOST IMPORTANT PART!

In the last section of the xorg.conf file, YOU MUST CHANGE the "SynapticsTrackpad" (or what shows up for those attempting this) to "ALPS"

Here's what my "ServerLayout" section looks like:

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"ALPS"
EndSection

-9mm (ouT)

---

### Post by 47th_Ronin on 2005-12-12
Very nice of you to post the solution, even without somebody helping you out... I have come cross so many post of people who have a problem, then later they reply with " Ohhh... I have fixed the problem"  without even telling what the solution was...

---

### Post by anil_robo on 2005-12-13
Most people visit forums just to be on the receivers end, it's so nice to see someone who believes in giving it out! :) Three cheers for Plastic9mm! :D

---

