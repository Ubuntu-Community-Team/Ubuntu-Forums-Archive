---
title: "Terminal auto-complete resets X"
date: 2009-01-18
forum: General Help
---

### Post by beejunk on 2009-01-18
So, I'm having weird issues with my terminal.  When I try to auto-complete (using TAB), if there is more than one potential choice for completing the letters I've already entered (for instance, if I enter just the letter 'a' and then hit TAB when I'm in a directory with many files that begin with 'a'), instead of doing nothing, or beeping, it actually resets X and kicks me back to the log-in screen (as if I'd hit control-alt-backspace).  It does not, however, do this when there is only one possible entry that could complete the filename.  In that case, it auto-completes the entry as expected.  Even more fun, if I have not entered anything at all into the line, and hit back-space, instead of doing nothing, it resets and kicks me back to the log-in screen.

This is very odd behavior, and it's incredibly annoying.  Any suggestions on what's going on here?  This is on Intrepid Ibex using GNOME.

---

### Post by beejunk on 2009-01-24
Both to bump this, and to add more details to the problem:

It seems this issue is not tied to auto-complete in and of itself.  It actually happens anytime I do anything in the terminal that would normally cause my computer to beep.  (What is the technical term for that?)  Instead, it resets my desktop.

---

### Post by beejunk on 2009-01-24
Okay, well, I've got this sort of solved.  Whatever the problem is, it has to do with the fact that I customized my xorg.conf file (I essentially imported it from Hardy in order to get all the functionality out of my Wacom tablet)  I discovered that when I put the default xorg.conf back in place, all my problems disappeared.  So that's good, except then I'm stuck with the standard Intrepid wacom setup, which does not use the tablets full range of functionality.  It's workable, though.

---

### Post by caffeine13 on 2009-01-25
I temporarily fixed the problem by changing to a different xterm program, but then found the problem popping up in some of my text editors as well. :(

----------

Okay, I think I might have fixed my particular problem by commenting out the "pad" wacom device in the xorg.conf file. 
...

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"pad"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"pad"
#	Option		"USB"		"on"
#EndSection

...

Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
	InputDevice     "stylus"	"SendCoreEvents"
	Inputdevice     "touch"	        "SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	#InputDevice	"pad"
	Inputdevice	"Synaptics Touchpad"
EndSection

---

### Post by beejunk on 2009-02-07
Well, I'm happy to report that the above mentioned fix is working for me, as well.  I now have the full Wacom functionality, without the odd bug.  Thanks!

---

