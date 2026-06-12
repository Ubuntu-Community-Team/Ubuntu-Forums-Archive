---
title: "Compiz Switching?"
date: 2007-12-04
forum: Desktop Effects &amp; Customization
---

### Post by ElEdwards on 2007-12-04
I have Compiz working very well in Gutsy on my laptop (Presario 2107us) but I occasionally have one issue.....

I'm set up to rotate the cube by either 1) clicking on the Workspace Switcher [on the taskbar] or 2) using Ctrl-Alt-LeftorRightArrow.  Once in a while after I close an app, the cube will rotate to another workspace without my intervention (I think).

Have I missed something in the configuration?  Perhaps something regarding the Synaptic Touchpad (I have disabled the tapping, btw).

Thoughts?  Help?  Thanks :)

---

### Post by Niklas Schröder on 2007-12-04
sometimes if you have another window open on another workspace it'll automatically jump to that window.  have you looked through the compiz settings to see if there's an option for your problem?

and how'd you disable the touchpad?  i can't get mine to shut off.  ;)

---

### Post by ElEdwards on 2007-12-04
Thanks :)
I'll look at the Compiz settings again.  The times the cube has surprised me with a flip, there were no other apps open.

Regarding disabling the Tapping on the Synaptics Touchpad.....
(*always* backup **xorg.conf** before making changes)
In **xorg.conf**, you'll find the Section that defines your Touchpad.  Add this **Option** line to the end of that section:
```
Section "InputDevice"
	<don't change your existing settings>
	**Option          "MaxTapTime"      "0"**
EndSection

```...then Ctrl-Alt-Backspace to restart the session.

This way, you can still use the touchpad to move the pointer without disabling that function but you won't accidentally tap and go where you don't want to go.

El

---

### Post by Niklas Schröder on 2007-12-04
yeah.  i'm sure there's a setting there somewhere.

but the xorg thing didn't do it.

here's my section for the touchpad...

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option          "MaxTapTime"      	"0"
EndSection

```

ideas?

EDIT: and *yes* i *did* restart x.

---

