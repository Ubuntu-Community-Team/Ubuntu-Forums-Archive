---
title: "USB Mouse (Rollermouse) buttons not working"
date: 2006-06-07
forum: Desktop Environments
---

### Post by JamesCC on 2006-06-07
Hi, I have a Contour Rollermouse (v2 classic) which under windows (no driver) behaves just like a USB mouse.  However under Ubuntu 6.06 whilst the mouse movement works fine, but buttons misbehave.

I have used xev to show the effects of pressing the buttons, and I am getting several buttons being pressed.  For example the left mouse button results in button "1" being pressed then button "9" being pressed.  The right mouse button results in "3" followed by button "9", and button "2".

Tried using evdev as the driver in the xorg.conf but that produced exactly the same results.

Any suggestions?  Thanks.  JamesCC

---

### Post by soknet on 2007-09-25
Did you get to make it run properly?

I'm having the same problem. But in Ubuntu 7.04

---

### Post by soknet on 2007-09-30
I got to make it run. I just used the USB to PS/2 adapter that came with the RollerMouse, connected it to the PS/2 port, and changed the settings button to standar/no driver.

---

