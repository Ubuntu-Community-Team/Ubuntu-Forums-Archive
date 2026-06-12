---
title: "Compiz freezes randomly with ATI X800XL"
date: 2006-07-26
forum: Desktop Environments
---

### Post by benjaminwr on 2006-07-26
Hi,

I have ben trying to find a solution in the forums all afternoon but I don't seem to find the problem.

I have installed Ati drivers from apt-get and xgl and compiz... all working fine ecept when I run commands from the gnome console. It doesn't allways happen but sometimes it compleetly freezes up my computer forcing me to do a hard reset.

I get a message at startup asking me what keyboard configuration I want to use (GNOME or X)I had to modify my keyboard options in System - Preferences - Keyboard to get pipes and my Super key working on a spanish keyboard since somwhere while installing, either compiz or xgl set my keyboard to US while writing the xorg.conf I was wondering if it was a crash related to input or wheather it is something else.

I also get this message very often in dmesg

[17181781.244000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[17181781.244000] [fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf 59f73c0 for 1261568 bytes (not allways the same location or number of bytes)

I am completly lost here and would apreciate help since I would like to start using xgl on a regular basis.

---

### Post by cptnapalm on 2006-07-26
I think the only way to get Xgl to work routinely would be to buy an nvidia card.

I have a laptop, so no nvidia for me....

I miss my wittle wobbly windows... :cry:

---

### Post by benjaminwr on 2006-07-26
Well if it helps...

I have a friend with a laptop that has installed XGL and it works fine, he has done in with ati and nvidia so maybe you should give it a try.

I have an update on my problem... this is the error message I get

The X system keyboard settings differ from your current GNOME keyboard settings... Please select... blah blah gnome settings or X settings

My gnome keyboard setup is set to es and pc104 keys in my gconf-editor

this is the section in xorg (autodetected)

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "es"

and technically i would have to add this

xmodmap /usr/share/xmodmap/xmodmap.es

to my startcompiz script to fix the shift+backspace bug but if I do shortcut keys and ALT CONTROL WIN etc... stop working

If I set it to 

xmodmap /usr/share/xmodmap/xmodmap.en  #en as oposed to es

I get shortcut keys but no spanish keyboard layout so no possible way of writing a complete command without going through all the keys again.

With any of these I still get ocasional lockups.

---

