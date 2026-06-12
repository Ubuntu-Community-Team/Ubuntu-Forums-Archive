---
title: "Problem with Logitech MX 620 under 9.04"
date: 2009-04-29
forum: General Help
---

### Post by r0y4l on 2009-04-29
Hi guys,

under 8.04/8.10 my Logitech MX 620 works perfectly, with in this thread mentioned method: 

[http://ubuntuforums.org/showthread.php?t=918471](http://ubuntuforums.org/showthread.php?t=918471)

Now, after the upgrade to Jaunty Jackalope 9.04 the mouse stopped working correctly, mouse movements, left and right click works fine. 

But if i use the scroll wheel in i.e. firefox it goes back in the page history, it looks like that the scroll wheel is now the back button.

I tried to get it working, but without any great success. Can anyone help me getting it working again?

If I use the normal mouse config the scroll wheel works but I can't use the back/next button on the mouse. He're my configs:

Config with working scrolling wheel but not working back/next button:

```
Section "InputDevice"
	Identifier     "Configured Mouse"
	Driver         "mouse"
	Option         "CorePointer"
	Option         "Device" "/dev/input/mice"
	Option         "Protocol" "ImPS/2"
	Option         "ZAxisMapping" "4 5"
	Option         "Emulate3Buttons" "true"
EndSection
```

Config with NOT working scrolling wheel and NOT working back/next button:

```
Section "InputDevice"
	Identifier  "Logitech MX620"
   	Driver      "evdev"
	Option	    "Device" "/dev/input/event3"
   	Option      "Name" "Logitech USB Receiver"
	Option 	    "Resolution" "800"
   	Option      "CorePointer"
   	Option      "evBits" "+1-2"
   	Option      "keyBits" "~272-287"
   	Option      "relBits" "~0-2 ~6 ~8"
   	Option      "Buttons" "10"
   	Option      "WHEELRelativeAxisButtons" "4 5" # vertical wheel
   	Option      "ButtonMapping" "1 2 3 8 9 10"
EndSection
```
 
Can anyone help out how to fix this problem?

---

### Post by JohnLau on 2009-06-15
I don't think you'll need to set anything to make it work in 9.04
All of its buttons are working well with the default Xorg.conf :popcorn:
Cheers,
JohnLau

---

### Post by keypox on 2009-06-21
> **JohnLau said:**
> I don't think you'll need to set anything to make it work in 9.04
All of its buttons are working well with the default Xorg.conf :popcorn:
Cheers,
JohnLau

no i dont thinks so.  I got mine working before but can't find the thread again. here is my default xorg.

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

well everything works in FF but not in nautilus.

---

### Post by JohnLau on 2009-07-09
For the scrolling wheel, it works fine everywhere, but for the back/forward button it only works in firefox...

---

