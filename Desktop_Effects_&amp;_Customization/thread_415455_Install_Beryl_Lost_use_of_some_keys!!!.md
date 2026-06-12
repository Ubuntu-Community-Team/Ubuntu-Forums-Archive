---
title: "Install Beryl Lost use of some keys!!!"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by ianb72 on 2007-04-20
I've just installed Beryl in Ubuntu 606 and its great apart from one big snag.

I have lost the use of the . on my number pad and the Delete key, also the Caps locks doesn't work anymore, How can I fix this??

My Xorg.conf say this: 
[HTML]Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection[/HTML]

Whereas the backup version says this:
[HTML]ection "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection[/HTML]

Do I just change the Xorg.conf? do the same as the backup version, if so how do I do that?

Cheers
Ian

---

### Post by eriK-B on 2007-04-21
i sort of had this problem too,
i installed beryl+emerald+xgl on my dapper
after i did that i lost my entire numpad.
i found a way to fix this though.

This only works if you use xgl!!!
in your xorg.conf file change (in the inputdevice section of your keyboard):

	Option		"XkbRules"	"xorg"
into:

	Option		"XkbRules"	"xgl"

then restart your system and it should work fine. at least it did for me.

hope this helps!:)

---

