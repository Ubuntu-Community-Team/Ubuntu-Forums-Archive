---
title: "Mouse wheel problems on ubuntu 8.10"
date: 2008-11-15
forum: Desktop Environments
---

### Post by d34th on 2008-11-15
I've updated to 8.10 from 8.04, and mouse wheel stopped working.
I'm using a logitech G3 mouse, and it worked properly...

```

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ExplorerPS/2"
#	Option		"ImputFashion"		"Mouse"
#	Option		"Emulate3Buttons"	"false"
#	Option		"ZAxisMapping"		"8 9"
#	Option		"Buttons" 		"9"
#EndSection

```

This is my xorg.conf mouse section, with this, the mouse worked perfectly, but now it seems that input devices config has moved to hal.
I've tried to configure hal, but nothing so far...

If I reconnect the mouse into the USB port, it works, but every time I start X, the wheel stops working

Any idea?

---

