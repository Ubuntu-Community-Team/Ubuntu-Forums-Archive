---
title: "Lost ability to scroll with touchpad"
date: 2008-11-09
forum: Desktop Environments
---

### Post by tcv on 2008-11-09
Hey folks,

Whilst attempting to update my xorg to allow the fglrx drive to work, I somehow lost the ability to perform vertical scrolling with my touchpad.

How can I begin to look into why? And also: How can I get it back? 

Running intrepid.

Here's my current xorg.conf, the input device section.

---

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"


THANKS!!!

---

