---
title: "Changing mouse button mappings on Evoluent Vertical mouse in Lucid"
date: 2010-09-14
forum: Desktop Environments
---

### Post by graphicsMan on 2010-09-14
Hi all -

As stated in the title, I'm trying to remap my mouse buttons.  They seem to be organized for browsing the web, but I want mine to match my style for writing code in emacs.  According to xev, 1 is left, 2 is scroll push (middle mouse), 3 is my center button (traditional right), 4 and 5 are scroll, (6, 7, unknown), 8 is my right-most button (back browser button), and 9 is my thumb button (forward browser button).  I'd love 1 to be left, 2 to be my center button, 3 to be my thumb button, 4 and 5 scroll, and turn off the rest.

I've tried modifying this in udev directly via a 90-local-xorg.rules file which looks like this:

```

ACTION!="add|change", GOTO="xorg_local_end"
KERNEL!="event*", GOTO="xorg_local_end"
 
ATTRS{ID_INPUT_MOUSE}!="1", GOTO="xorg_local_end"
ATTRS{ID_MODEL}!="Evoluent_VerticalMouse_3", GOTO="xorg_local_end"
 
ENV{ID_INPUT.tags}="evoluent_vertical_mouse"
# ENV{x11_options.Emulate3Buttons}="no"
# ENV{x11_options.EmulateWheelButton}="0"
# ENV{x11_options.ZAxisMapping}="4 5"
# #ENV{x11_options.ButtonMapping}="1 2 2 4 5 6 7 3 8"
# ENV{x11_options.ButtonMapping}="1 0 2 4 5 6 7 0 3"
 
LABEL="xorg_local_end"

``` 
I used to try to set the x11_options directly here, but somewhere during my extensive google searches I found that this is deprecated and won't work in Lucid.  Now instead, I have added the ID_INTPUT.tags setting a tag that I can (hopefully) match against in an xorg.conf.d file, which I have at
/etc/X11/xorg.conf.d/20-evoluent.conf and looks like:

```

Section "InputClass"
	Identifier "Reset vertical mouse buttons"
	MatchTag "evoluent_vertical_mouse"
	Driver "evdev"
	Option "Emulate3Buttons"	"off"
	Option "EmulateWheel"		"off"
	Option "ZAxisMapping"		"4 5"
#	Option "ButtonMapping"		"1 2 2 4 5 6 7 3 8"
	Option "ButtonMapping"		"1 0 2 4 5 6 7 0 3"
EndSection

```

I feel like I've tried dozens of things by now, and I'm ready to seek your help :)  My xorg.0.log output is 

```

II) config/udev: Adding input device Kingsis Peripherals  Evoluent VerticalMouse 3  (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Kingsis Peripherals  Evoluent VerticalMouse 3  (/dev/input/event4)
(**) Kingsis Peripherals  Evoluent VerticalMouse 3 : Applying InputClass "evdev pointer catchall"
(**) Kingsis Peripherals  Evoluent VerticalMouse 3 : always reports core events
(**) Kingsis Peripherals  Evoluent VerticalMouse 3 : Device: "/dev/input/event4"
(II) Kingsis Peripherals  Evoluent VerticalMouse 3 : Found 9 mouse buttons
(II) Kingsis Peripherals  Evoluent VerticalMouse 3 : Found scroll wheel(s)
(II) Kingsis Peripherals  Evoluent VerticalMouse 3 : Found relative axes
(II) Kingsis Peripherals  Evoluent VerticalMouse 3 : Found x and y relative axes
(II) Kingsis Peripherals  Evoluent VerticalMouse 3 : Configuring as mouse
(**) Kingsis Peripherals  Evoluent VerticalMouse 3 : YAxisMapping: buttons 4 and 5
(**) Kingsis Peripherals  Evoluent VerticalMouse 3 : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Kingsis Peripherals  Evoluent VerticalMouse 3 " (type: MOUSE)
(II) Kingsis Peripherals  Evoluent VerticalMouse 3 : initialized for relative axes.

```

Please let me know if there's something else I can post to assist you to assist me :)

Thanks!

---

### Post by graphicsMan on 2010-09-15
No one knows?  Does anyone understand how to implement xorg rules that are called by udev?  It's woefully undocumented, and it seems that if it's being used in Ubuntu releases, there should be information about it somewhere.

---

### Post by graphicsMan on 2010-09-15
Actually, my method worked.  Crazy.  Simply required a full reboot (which is a little annoying, but hey, I'll take it).

Hope this helps someone else.

---

### Post by smiley1962 on 2011-04-29
I just got this mouse and due to my native language (dutch) i'm struggling
with this post to do the remapping of the buttons, could someone tell me what I have to edit to get all of the 5 buttons to work? 

The buttons should have the following functions(as default in windows):
top one: left click
schrollwheel: drag and scroll
middle button: double click
bottom one: richt click
thumb button: Back ( it does undo the previous action) and in firefox page back 

thanks in advance, im still using maverick but probably natty within a week

---

