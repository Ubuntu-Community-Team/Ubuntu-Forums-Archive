---
title: "How to use the other buttons on my mouse in Compiz?"
date: 2008-03-01
forum: Desktop Effects &amp; Customization
---

### Post by sroark on 2008-03-01
Hi, I am using a Microsoft mouse with a scrollwheel in the middle that can be pushed in, and pushed to the left or right as well to be used a button. There is also a small button on the side. I want to use these buttons to control my cube with Compiz Fusion, and I have found where you do so, but I can't get any buttons after "Button3" to do anything. Any advice on what needs to be done to use the rest of the buttons on my mouse? Thank you.

---

### Post by spoilerhead on 2008-03-01
how does your /etc/X11/xorg.conf look like?


heres my mouse snippet that works for my logitech mx518 (8 buttons + scrollwheel)

```

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "evdev"
        #Option      "CorePointer"
        Option      "SendCoreEvents" "true"
        Option      "Name" "Logitech USB-PS/2 Optical Mouse"
        Option      "Emulate3Buttons" "true"
        Option      "ZAxisMapping" "4 5 6 7"
        Option      "Buttons"   "12"
        Option      "Resolution"    "400"
        Option "AllowMouseOpenFail" "true"

EndSection

```

note that i removed core pointer from it, as sometimes i got my mouse unplugged and use the touchpad 

theres also a tutorial for it in the tutorials section

---

### Post by sroark on 2008-03-01
K, here is what mine says:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

---

