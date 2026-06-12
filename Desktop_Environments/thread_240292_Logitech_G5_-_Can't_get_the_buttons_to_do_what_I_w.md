---
title: "Logitech G5 - Can't get the buttons to do what I want"
date: 2006-08-20
forum: Desktop Environments
---

### Post by c_x on 2006-08-20
[COLOR="Red"]Never mind, I solved the problem :D[/COLOR]
Okey, today I bought a Logitech G5 Mouse.
This is in xorg.conf:
```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "evdev"
	Option	    "CorePointer"
	Option	    "Name" "Logitech USB Gaming Mouse"
	Option	    "Buttons" "8"
	Option	    "ZAxisMapping" "4 5 7 8"
EndSection
```
And this in ~/.xbindkeysrc: (Yes, xbindkeys is installed and is in startupscript)
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[_L_eft]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Page_Down]""
  m:0x0 + b:7
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Page_Up]""
  m:0x0 + b:8

```
What happens:
Tilt-left = forward (yes ](*,) )
Tilt-right = back
Back-button = somtimes actiong like left-click and sometimes like "select, but don't click"

What I want to happen:
Tilt-left and right = navigate tabs in firefox
Back-button = back in firefox and nautilus

Thanks in advance!

---

### Post by vyruss on 2006-08-20
> **c_x said:**
> [COLOR="Red"]Never mind, I solved the problem :D[/COLOR]
Okey, today I bought a Logitech G5 Mouse.


This is not very constructive. If you could at least mention what you did to solve the problem it might be helpful for somebody who has the same problem.

---

### Post by tomski on 2006-08-20
have you got iwheel installed too

i think this will help as i have a multi button mouse & i add that code to xorg.conf (as you have) after installing iwheel


EDIT:
sorry i did not see that you solved the problem


i must be colour blind!!

---

### Post by phunkycow on 2006-08-22
I did some search, hope this will work for you (I haven't tested it as I don't own a G5).

Go to [http://www.adterrasperaspera.com/blog/2006/06/20/logitech-g5-review-under-linux/](http://www.adterrasperaspera.com/blog/2006/06/20/logitech-g5-review-under-linux/)

and scroll down to "How to get it to work in Linux".

Good luck! :)

---

### Post by c_x on 2006-08-22
> **vyruss said:**
> This is not very constructive. If you could at least mention what you did to solve the problem it might be helpful for somebody who has the same problem.

Sorry, this is how I got it to work:

My code was:
```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "evdev"
	Option	    "CorePointer"
	Option	    "Name" "Logitech USB Gaming Mouse"
	Option	    "Buttons" "8"
	Option	    "ZAxisMapping" "4 5 7 8"
EndSection
```

I think when you have evdev as the driver (I must have it, because else it doesn't work with fglrx) it won't obey the options, so I just mixed and trixed with ~/.xbindkeysrc til it worked, here is my final output:
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Page_Down]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Page_Up]""
  m:0x0 + b:7

```

---

### Post by muxecoid on 2007-05-13
Same problem here. I want the side button to work as Ctrl+Alt+Left Button (Beryl Desktop switching).

---

