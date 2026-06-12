---
title: "Multiple XKB layouts that share the same symbols file ... via xorg.conf"
date: 2006-03-11
forum: Desktop Environments
---

### Post by branco on 2006-03-11
First of all, let it be said that I know how to set up layouts using GNOME's keyboard config dialog, but I need this to work so I can use E17, XFCE and other desktops that lack GUI for layout selection and switching.

I've searched a lot on this one, but (still) no luck. I need someone to explain to me how to achieve this:

I need to add two keyboard layouts that share the same symbols file (namely "cs"). Serbian uses two alphabets and both are included in the file "/etc/X11/xkb/symbols/cs".

I edit "xorg.conf" to make it look like so:

<paste>
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us,cs"
	Option		"XkbOptions"	"grp:rwin_toggle"
EndSection
</paste>

Note that the "XkbLayout" is currently set to "us,cs". The "cs" symbols file contain (among other things) "basic", "latin", etc. symbol groups. How can I have both e.g., "basic" and "latin" layouts?


TIA!

---

### Post by tsphan on 2007-02-22
Here is my section for 2 US keyboard layouts (using a basic symbol set and an international set), with a Vietnamese keyboard layout.

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,us,vn"
        Option          "XkbVariant"    "basic,intl,basic"
        Option          "XkbOptions"    "lv3:ralt_switch,grp:ctrls_toggle,grp_led:scroll"
EndSection

So for the Serbian keyboard layouts, I found these settings to work for you:
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,cs,cs"
        Option          "XkbVariant"    "basic,basic,latin"
        Option          "XkbOptions"    "lv3:ralt_switch,grp:ctrls_toggle,grp_led:scroll"
EndSection

You can try it out first with the command: 
"setxkbmap -option lv3:ralt_switch,grp:ctrls_toggle,grp_led:scroll us,cs,cs basic,basic,latin"
Just press Left Ctrl and then Right Ctrl at the same time, and the scroll lock light should come on for the serbian keyboards.

---

