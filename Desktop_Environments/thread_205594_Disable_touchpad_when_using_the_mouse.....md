---
title: "Disable touchpad when using the mouse...."
date: 2006-06-28
forum: Desktop Environments
---

### Post by mtpadilla on 2006-06-28
Hello. Would anyone happen to know of a way to have Gnome automatically disable the touchpad when a USB mouse is attached? (and then make it active when the mouse is disconnected) I have an IBM T42 and this would be quite handy as the touchpad gets into the way sometimes when I'm typing and using a mouse, but of course need it when I'm not using a mouse.

Hmmm...

Thanks in advance!

---

### Post by kecsap on 2006-11-13
I have found the following howto: [http://www.wlug.org.nz/HotPlugNotes](http://www.wlug.org.nz/HotPlugNotes)

---

### Post by drowsy on 2006-12-23
I hate using touchpad :) Solution is simple : 

Compile touchpad as a module in the kernel(psmouse)
and then write appropriate UDEV rules(__very__ easy). Mine are here : 
> cat /etc/udev/rules.d/010_local.rules

ACTION=="add", KERNEL=="event*", SUBSYSTEM=="input", \
SYSFS{product}=="USB-PS/2 Optical Mouse", NAME="input/mx518", RUN+="/sbin/rmmod psmouse"

ACTION=="remove", KERNEL=="event*", SUBSYSTEM=="input", \
SYSFS{product}=="USB-PS/2 Optical Mouse",  RUN+="/sbin/modprobe psmouse"

"add" means that you plug a mouse, "remove" means you unplug it. Good luck !

---

### Post by iberger on 2007-10-15
how do you:

Compile touchpad as a module in the kernel(psmouse)

I have a Lenovo N100 and the touchpad is driving us crazy

any help would be greatly appreciated
thanks
i_berger<at>yahoo.com

---

### Post by ugm6hr on 2007-10-16
@iberger:
If the Touchpad issue is related to typing (and accidentally touching it) - then syndaemon is a slick solution, and very easy:
[http://ubuntuforums.org/showpost.php?p=3136787&postcount=8](http://ubuntuforums.org/showpost.php?p=3136787&postcount=8)

---

### Post by burgerearl on 2007-12-18
Can anyone answer the followup question on how to compile touchpad as a module? I would love to get this functionality, but that is way over my head.

---

### Post by Arthur Archnix on 2008-01-21
Yeah... that's over my head too. I did it in a much simpler way, but I only know how to do it on Gnome under 7.10. It's not perfect, but here it is:

1. Turn on SHMConfig in xorg.conf
```
gksudo gedit /etc/X11/xorg.conf
```
and add the bold line:
> Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	**Option		"SHMConfig" 		"on"**
You'll need to restart 'X' at this point, by either logging out or hitting Ctrl+Alt+Backspace

2. Go to >System >Preferences >Removable Drives & Media, then to the last tab called "Input Devices", and check the box that says run a program when mouse is plugged in.
Paste this command in there:
```
synclient touchpadoff=1
```
Well, now you should find that next time you plug a mouse in, your touchpad is turned off. Ok, so what about you remove the mouse? Unfortunately, it isn't turned back on automatically. So we make a shortcut to turn it back on. I'm not using the F10 key, so I'm gonna use that key, but you can make it another if you like.

3. Open up gconf-editor (type that in a terminal) and go to >apps >metacity >keybinding_command

Beside command one, click on the value space and paste this in there:
```
synclient touchpadoff=0
```
Now click global_keybindings (just above keybinding_command) and click on run_command_1, click on the value and enter this:
```
<Control>F10
```
You can replace control if you like, or just use F10, or some other combination.

That's it.

---

### Post by sojusnik on 2008-02-18
Hi,

I've found a tutorial how to disable the touchpad when the USB Mouse is plugged in, but can't really understand what to do, I'm quite new to Ubuntu.

Instruction: [http://linuxtidbits.wordpress.com/2007/10/27/switch-automatically-mouse-and-touchpad/](http://linuxtidbits.wordpress.com/2007/10/27/switch-automatically-mouse-and-touchpad/)

It would be great, if someone could explain this tutorial more detailed to a newbie.

Thx in advance!

---

### Post by Arthur Archnix on 2008-02-28
I just followed it and it's a much more elegant and simple solution than my own workaround. His comments about running the script are unecessary, at least for me, because you can achieve the same functionality by adding one line to your session startup.

So, to achieve the results in that admirable link, do the following:
```
gksudo gedit /etc/udev/rules.d/10-local.rules
```
An empty file should open, and you should paste these lines:
```
ACTION=="add", SUBSYSTEM=="input", ID_CLASS="mouse", RUN+="/usr/bin/synclient touchpadoff=1"
ACTION=="remove", SUBSYSTEM=="input", ID_CLASS="mouse", RUN+="/usr/bin/synclient touchpadoff=0"
```
Restart, and voila. Now, if you want to have your touchpad disabled while you type, simply add this to your sessions:
```
syndaemon -i 1 -d
```
Go to >system >preferences >sessions, click add, above is the command and you can give it a name and comment that make sense to you. You will need to restart x for this to take effect I believe.

---

### Post by Valkoinenpulu on 2008-04-16
The touchpad disabling with USB mouse works great for me... But only when the mouse is plugged in after gnome has fully loaded.

Is there anyway to make it detect during startup if the usb mouse is present to disable touchpad? Otherwise you have to plug it out and back in to get the touchpad off... Not an earth shattering problem but annoying nonetheless

Anybody know what to add to /etc/udev/rules.d/10-local.rules to make this work?

---

### Post by raequin on 2008-05-09
I can not disable my touchpad in any way through Ubuntu.  I am running Hardy.  The only way I can get anything at all to change with the touchpad is to use the Fn+F7 button that came with the laptop to turn off the touchpad.  I would appreciate any help with this problem.

I've edited xorg.conf, tried syndaemon, gsynaptics, and System->Preferences.

I am not trying to use an external mouse.  I just want to disable the touchpad for when I am typing.

Thanks.

---

### Post by boteeka on 2008-06-14
This is an (possibly) easily fixable problem as the folks explained before me. It's not that it cannot be fixed through different system file hacks, the problem is that it cannot be done by checking a checkbox which says "Disable touchpad while mouse is present" and another one "Disable touchpad while typing". This way the user can decide which functionality he wants enabled and that's it. Everybody is happy. I can't imagine that somebody who uses a laptop doesn't has this problem considering the growing number of laptops sold. So, this issue regards quite a large group of users. I think this settings should go under Preferences->Mouse preferences->Touchpad.

---

### Post by undertakingyou on 2008-06-20
> **boteeka said:**
> This is an (possibly) easily fixable problem as the folks explained before me. It's not that it cannot be fixed through different system file hacks, the problem is that it cannot be done by checking a checkbox which says "Disable touchpad while mouse is present" and another one "Disable touchpad while typing". This way the user can decide which functionality he wants enabled and that's it. Everybody is happy. I can't imagine that somebody who uses a laptop doesn't has this problem considering the growing number of laptops sold. So, this issue regards quite a large group of users. I think this settings should go under Preferences->Mouse preferences->Touchpad.

A great suggesting.  The X11 system has come a long way and will continue to grow.  Have you submitted some sort of feature request to them to get this to happen?

---

