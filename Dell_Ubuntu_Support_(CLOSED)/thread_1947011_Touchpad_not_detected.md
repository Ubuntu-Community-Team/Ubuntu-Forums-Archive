---
title: "Touchpad not detected"
date: 2012-03-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RobikShrestha on 2012-03-25
I can use my touchpad for single clicking, double clicking and moving the pointer but not for scrolling and zooming.

In the program, "mouse and touchpad", there is no tab for "touchpad". I   want to enable vertical and horizontal scrolling. I also want two  finger zooming. How do I do that?

I am using a Dell Inspiron N 5110 laptop. The OS is 64-bit Ubuntu 11.10.

The output of 

xinput list 

is:
[I]
Virtual core pointer id=2 [master pointer (3)] 
 Virtual core XTEST pointer id=4 [slave pointer (2)] 
 PS/2 Generic Mouse id=13 [slave pointer (2)] 
Virtual core keyboard id=3 [master keyboard (2)] 
Virtual core XTEST keyboard id=5 [slave keyboard (3)] 
 Power Button id=6 [slave keyboard (3)] 
Video Bus id=7 [slave keyboard (3)] 
Video Bus id=8 [slave keyboard (3)] 
Power Button id=9 [slave keyboard (3)] 
Sleep Button id=10 [slave keyboard (3)]
 Laptop_Integrated_Webcam_HD id=11 [slave keyboard (3)]
 AT Translated Set 2 keyboard id=12 [slave keyboard (3)] 
 Dell WMI hotkeys[/I]

I don't see my touchpad in this output.

I can use gpointing-devices for middle mouse button emulations and other  stuffs but I still can't use the touchpad for scrolling and zooming.

---

### Post by fred0843 on 2012-03-26
I have the same problem with a m5030.They use a alps touchpad.You may need driver for it.

---

