---
title: "Mouse support?"
date: 2005-12-25
forum: Desktop Environments
---

### Post by Jeff12088 on 2005-12-25
I just installed Ubuntu 5.10, running fine, logged in using keyboard but I just can't move the mouse...
It's not a fancy mouse, it's a very old mouse, not a PS2 one.
It has a bigger plug than the ones we have now.
Many of us may still use them, anyway to fix this?

I can't switch a mouse because the motherboard only supports these kind of old mouse.

---

### Post by Jeff12088 on 2005-12-25
Bumpy

---

### Post by Sokraates on 2005-12-25
[QUOTE=Jeff12088]I just installed Ubuntu 5.10, running fine, logged in using keyboard but I just can't move the mouse...
It's not a fancy mouse, it's a very old mouse, not a PS2 one.
It has a bigger plug than the ones we have now.
Many of us may still use them, anyway to fix this?

I can't switch a mouse because the motherboard only supports these kind of old mouse.[/QUOTE]

I've never heard of non-USB-mice not being recognized by linux. If noone has a more productive proposition, you could try an adapter to use the serial port. It's a workaround I use for my USB-mouse (USB-to-PS2). Though, my mouse had the adapter included, so I didn't have to buy a new one.

---

### Post by Sef on 2005-12-25
Have you checked your BIOS to make sure it is the mouse is set to serial?

---

### Post by Jeff12088 on 2005-12-26
Yes. The correct name is Serial Mouse. :p 
I will check that. I had Windows ME perviously on this computer and had no problems with the mouse, but I will check that,
Any other possibilities or solutions would be help ful :D ;)

---

### Post by xmastree on 2005-12-26
Serial mouse. Ok, what you need to do is edit your xorg.conf file.

Back up your original one first, from a terminal, type```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Then:```
sudo gedit /etc/X11/xorg.conf
```

Find this section:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

And change it to:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
[COLOR="Red"][B]	Option		"Device"		"/dev/ttyS0"
	Option		"Protocol"		"Microsoft"[/B][/COLOR]
	Option		"Emulate3Buttons"	"true"
EndSection
```
Or /dev/ttyS1 if it's in COM2

**[COLOR="Red"]EDIT: Be sure to use ttyS0 (that's tty-CapitalS-Zero), not ttys0. I made that mistake once and it locked up my keyboard. My only option was to boot from a live CD to edit it. I couldn't even ctrl-alt-F1 to a console.[/COLOR]**

---

### Post by Jeff12088 on 2005-12-26
Whoo.. Thanks alot. It worked right off the bat.. :) 

Thats why I love Ubuntu :D

---

### Post by xmastree on 2005-12-26
[QUOTE=Jeff12088]Whoo.. Thanks alot.[/QUOTE]
\\:D/

You're Welcome.

---

### Post by christhemonkey on 2006-01-14
cheers :)

---

### Post by Icedude1978 on 2006-03-27
[QUOTE=Jeff12088]Whoo.. Thanks alot. It worked right off the bat.. :) 

Thats why I love Ubuntu :D[/QUOTE]

Did that command work with you in Kubuntu? :confused: 

I can't get my serial mouse to work in Kubuntu. ](*,)

---

### Post by xmastree on 2006-03-27
[QUOTE=Icedude1978]Did that command work with you in Kubuntu? :confused: 

I can't get my serial mouse to work in Kubuntu. ](*,)[/QUOTE]

It should do. It's an X thing rather than a desktop thing. In other words, the mouse driver is loaded before the desktop environment. You can use it on the login screen.

Does your mouse work before you login and load KDE?

---

### Post by Icedude1978 on 2006-03-28
No, it never worked.

---

### Post by xmastree on 2006-03-28
So it's nothing to do with KDE then. If you're sure the mouse itself is ok, and you've edited xorg.conf as sugested above, I can only think that your serial port isn't /dev/ttyS0
Is there another serial port? Try the mouse in the other one.

---

### Post by Icedude1978 on 2006-03-28
The mouse is ok, I'm using it on Windows right now but the problem was that I can't access the xorg.conf like suggested. I always get the message "command unknown" when I type "sudo gedit /etc/X11/xorg.conf".

---

### Post by xmastree on 2006-03-28
[QUOTE=Icedude1978]"sudo gedit /etc/X11/xorg.conf".[/QUOTE]D'Oh...
**gedit** is the gnome editor. I'm not sure what the default text editor is in KDE, possibly kedit (that's a guess).

---

### Post by Icedude1978 on 2006-03-28
I heard it was kate but I'll try that.

---

### Post by Icedude1978 on 2006-03-28
I found out I didn't have kate installed so I installed it using sudo apt-get install kate

Now I have another problem. Now I get the message : 
kate: ERROR: communication problem with kate, it probably crashed

By the way, do you know how to activate the "K" menu left bottom of the screen with the keyboard? In windows you activate the start button with ctrl-esc.

P.S.: I filled in this reply in Konqueror but it's hard only using your keyboard.

---

### Post by Icedude1978 on 2006-03-28
Woohoo, it works!! I forgot to enter my password after installing kate. I entered the necessery device in my xorg.cof too so my mouse works too. Now I can start learning the others!

Oh, I'm already installing the necessery updates too now.

---

### Post by xmastree on 2006-03-28
[QUOTE=Icedude1978]Woohoo, it works!! 

my mouse works too.[/QUOTE]
Great! 8)

---

### Post by dheerajsp on 2006-10-05
good, so i found this thread.

i got a logitech serial mouse, ball mouse. i did the gedit thing mentioned earlier, but that didnt help. i guess u have to restart the comp, which i did, but still, no mouse movement.!!!!


edit: problem solved.

---

