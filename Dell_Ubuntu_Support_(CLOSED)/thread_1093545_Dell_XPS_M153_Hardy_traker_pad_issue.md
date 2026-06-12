---
title: "Dell XPS M153 Hardy traker pad issue"
date: 2009-03-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by probe200 on 2009-03-11
I've read lots of posts on the this subject and I've tried the fixes. The symptoms have been reported before - on many forums. But I can't fic this fault.

I'm running hardy on an XPS M1530 I bought about 3 weeks ago. I got rid of the msft bloatware. I installed hardy and I'm running KDE 3.5. 

I'm using a USB Mouse and verything works fine except the keyboard and built in tracker pad. 

1) the tracker pad cursor jumps around and opens windows randomly - the cursor is out of control
2) the keyboard appears to have sticky keys so that the cursor will every few minutes freeze and then say after 10 seconds free up and repeat a symbolllllllllllllllll like this.

I've tried editing xorg.conf, and also editing the grub menu.lst file. But this does not work. 

Here's my menu.lst wher you can see I added the i8042.noumx=1 addition.

## ## End Default Options ##

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=1e49caeb-a30d-458d-968a-d9bb0940f9c5 ro quiet splash i8042.noumx=1
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

here's xorg.conf.....

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option  	"SHMConfig" "true"
	Option 		"MaxSpeed" "0.99"
	Option 		"AccelFactor" "0.08"
EndSection

I added the last 3 lines as recommended in a post.

here's what dmesg reports about the mouse....

[  566.144751] psmouse.c: Failed to reset mouse on isa0060/serio1
[  566.148481] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[  566.173077] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[  566.182032] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[  566.218238] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[  566.235540] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[  566.252633] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[  566.284963] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[  566.707704] printk: 17 messages suppressed.
[  566.707714] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[  567.311921] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input12
[  567.500156] psmouse.c: Failed to enable mouse on isa0060/serio1


Can anyone help?  I'm getting a bit desparate.

---

