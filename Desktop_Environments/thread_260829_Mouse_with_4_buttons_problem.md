---
title: "Mouse with 4 buttons problem"
date: 2006-09-19
forum: Desktop Environments
---

### Post by parapcros on 2006-09-19
Hi! First, sorry for my ver very bad english. Second, congratulations for this exceptional work!

I use Ubuntu for a long time (4.10, for trying and 5.04 for use). And i always have the same problem: i can't use the side button of my mouse, a Logitech. I search in forums, webs, blogs, wikis... Nothing help me.

I configure the xorg.conf to use the 4 buttons, and all seems well. The mouse have the 2 normal buttons, scrool + click (middle button) and a side button (only one). I can't configure the last.

I use the xev utility to see the mouse events and.. i can't see an event of the 4 button! It seems than not exists! What i can do? The problem isn't configuration; the button don't exists for my Ubuntu.

Thanks for all and sorry for my english ;)

---

### Post by Jordash on 2006-09-19
I'm having this same problem, my mouse is a Logitech G5, any ideas?

---

### Post by kick6 on 2006-09-19
can you post your xorg.conf?

---

### Post by parapcros on 2006-09-20
of course...

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
#	Option		"Protocol"		"MouseManPlusPS/2"
	Option		"Buttons"		"6"
	Option		"ButtonsMapping"	"1 2 3 6"
	Option		"ZAxisMapping"		"4 5"
#	Option		"Emulate3Buttons"	"true"
EndSection

```

The commented options are for try differentets configurations. I think that all is good. When i use xev to see mouse events and to identify the button numbers, i never see the event of the 4 button.

My mouse is an old Logitech Cordless MouseMan Wheel. I want to change it but, if i can't configure this, i sure can't configure the new mouse.

PD: Sorry for my english and thanks

---

### Post by kick6 on 2006-09-20
I don't know for sure if this will work, but its worth a shot.  I use a microsoft intellimouse exploder, and this is what I had to do to get all the buttons to work:

1. ```
cat /proc/bus/input/devices
```
this should return some info about your mouse that looks like

```
I: Bus=0003 Vendor=045e Product=008c Version=0057
N: Name="Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A"
P: Phys=usb-0000:00:1d.0-1.2/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse0 [COLOR="Red"]**event3**[/COLOR] ts0
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=1c3
```

the important part you need to note is in red.  Just write it down for a moment.

2. open up xorg.conf, and your mouse section should look like this

```
Section "InputDevice"
Identifier "Configured Mouse 2" #use an alternate name so if this config tanks the mouse still works
Driver "evdev"
Option "Device" "/dev/input/[COLOR="Red"]**event3**[/COLOR]"
Option "SendCoreEvents" "true"
Option "Buttons" "6"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "no"
EndSection
```

See if that at least makes it so you can see button 4 in xev.

---

### Post by Mandoscottie on 2006-09-21
I have the exact same mouse as you kick6 (MS intellieye explorer) and the side buttons not working is a pain. 

Im at work atm but im going to try out what you said tonight so heres hoping :) 

cheers bud :)

---

### Post by parapcros on 2006-09-21
No, i can't see button 4. I change de xorg.conf, but nothing happens. The mouse still works but button 4 don't exists. I don't see any chage between the old and the new configurations :(

Some new ideas? Thanks :)

---

### Post by parapcros on 2006-09-26
oh... Nothing else? ;) I whant my button!! xD

---

### Post by mc^2 on 2006-09-26
maybe you should give this a try:

[https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons](https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons)

greetings

---

### Post by parapcros on 2006-10-01
Thanks for the link and sorry for this late reply...

I install the imwheel and modify the xorg.conf, but the 4th button doesn't appear. I read in the imwheel homepage that

> IMWheel supports these non-standard buttons and/or wheel operations by allowing the user to map their input to key combinations which can vary
depending on the application in use

I understand that this program can help me to MAP non standard buttons, but it can't "show" me the buttons if the Operative System can't.

---

### Post by PlancksCnst on 2007-02-04
Hi, I just found this post.  I have the same Logitech Cordless Mouseman Wheel, with the same problem.  I can't get the side button to show up in xev.  I have a post about it [here]("http://www.ubuntuforums.org/showthread.php?p=2088586#post2088586").  Someone gave me similar info (about imwheel et. al.), and obviously this doesn't help if xev can't even see the event.

Did you get anywhere with this?

---

### Post by VvWolverinevV on 2008-02-22
*Bump*

I have the same problem.

---

