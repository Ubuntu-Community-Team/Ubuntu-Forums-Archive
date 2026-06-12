---
title: "Keyboard suddenly died"
date: 2005-12-26
forum: General Help
---

### Post by André on 2005-12-26
Hi everybody,

ten minutes ago my Kubuntu crashed and i had to hard reboot  it (pressing the power button ;-)).

When it restarted my laptop keyboard suddenly stopped working. So i tried to plug in a second one via USB... no go. Rebooted... no go. Tried that more than once...

I noticed that it worked in BIOS so i started my old Windows to write this message.

Any ideas? Mouse is working...

Greetings and merry Chrsitmas
André

---

### Post by jeremy on 2005-12-26
The only thing I can think of is that you check your
/etc/X11/xorg.conf

Here is the keyboard part of mine (I have a 105 key spanish keyboard) for comparison:
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

---

### Post by André on 2005-12-26
Hi,

thanks for the quick reply. I will take a look on the xorg.conf from a LiveCD because i cannot even swith in command line mode :-(

The xorg.conf worked for two months before but maybe it got f****d up by the crash.

Thanks for your answer. I will report back ;-)
André

---

### Post by André on 2005-12-28
Hi,

i used the Dapper Live CD to check my files. Everything seems okay here... i am reinstalling right now :-(

Greetings
André

---

