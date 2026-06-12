---
title: "Mutli-seat support"
date: 2006-04-16
forum: Desktop Environments
---

### Post by Intangir on 2006-04-16
I am trying to set up Multi-seat (multihead, dual head) support for Xorg7modular

most of the stuff is working for the most part

the problem im having is with my keyboards
i have 2 keyboards, a ps2, and a usb

from what ive read you have to use the 'evdev' keyboard driver to pick between specific keyboards, the kbd driver doesnt let you pick guess? just uses them all

so i tried to use it, i found several tutorials on the internet and most are vague, outdated or just utterly useless, some are for xfree86 i think.. anyway here are the config options i have tried, and what happened:

Identifier	"Generic Keyboard"
#kbd doesnt let me pick specific keyboards
#Driver "kbd"

#im using evdev like this, this seems to be the 
# way your supposed to do it on xorg7 (ive seen other ways that errored on 7)
Driver		"evdev"           

# when i use Dev Phys using the phys string i found in
# /proc/input/devices or something like that it
# crashes on startup, locks up, gives me a blackscreen and is completely
# nonresponsive, i have to hit the reset button..
#	Option		"Dev Phys"	"isa0060/serio0/input0"


# when i use Device it just doesnt seem to use it..
# i got the device string from the /proc/input/devices or whatever..
# it said the ps2 is event0 and the usb is event2, but when
# i boot up BOTH keyboards work, and if it switch vts the ONLY
# the USB works! even though its the one thats not supposed to work
# on my main screen
#	Option		"Device" "/dev/input/event0"

# when i left this in on both serverlayouts for both seats it kept crashing
# as soon as i logged, in then it would restart gdm again.. 
#	Option		"CoreKeyboard"

# this stuff was default, seems to have no bearing on multi-seat issues
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"



so as you can see ive tried several different configs for the keyboard and none of them have really worked right..

i havent been able to find ANY INFORMATION ANYWHERE about evdev configuration options
i cant find what evdev is, who made it, where it comes from.. anything.. 
when i do google searches tons of stuff comes up but its mostly people having issues with it.. but also it seems to be the only way to do multiseat..


if anyone has gotten multi-seat working with combinations of usb and ps2 keyboards please help me out, paste your xorg config, or tell me if you know of any other configs i have to change, or packages i need to install.. also make sure to tell me what versions you are using

it seems like each version has differences, older versions had patches which are no longer needed and their configs dont work the same anymore..

FUN.. im surprised anyone has ever gotten this working..

---

### Post by bernt_ on 2006-08-20
I have a multiseat with 4 displays working :-)
(first breezy, now dapper)

I used the device option with the evdev driver.

and also this parts from evdev man page:

         Driver "evdev"
         Option "evBits"  "+1"
         Option "keyBits" "~1-255 ~352-511"
         Option "Pass"    "3"
         Option "XkbModel" "evdev"

but I had to modify gdm. :(  (diff file is attached)

---

### Post by andersja on 2008-05-13
[[IMG]http://brainstorm.ubuntu.com/idea/3442/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/3442/)

---

