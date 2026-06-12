---
title: "Extended display issues"
date: 2022-01-22
forum: Desktop Environments
---

### Post by reavermyles on 2022-01-22
I was hoping for some help here. I think I'm using lubuntu 20.04 or lubuntu 21. My laptop has hdmi and vga and I utilize both for displays. But the displays screws up and now essentially I cannot access ANYTHING so darn frustrating the laptop will not revert back to using its own screen (which works fine) once I unplug the extended displays. So I want to add or subtract a monitor, The screens turn into the extended display so every window that pops up, Pops up on the screen that's not on. The screen that has the bar at the bottom to access everything on computer is on the other screen...in accessible. No matter what I do the laptops screen will not turn back to normal and the other 2 displays keeps just showing one at a time (I have to change setting manually which is fine but inaccessible) and when I do ctrl T to try to bring up the terminal...it pops up on the wrong screen!!! So I can't use the computer because the SETTINGS for the monitors is messed up...but it's the 21st century people! There is no reason the laptops settings shouldn't be automatically reverting back to it original screen display settings once the HDMI or VGA or what ever cable is un plugged. My question is how to I access the terminal or fix this issue? Sorry if it is convoluted but the issue is weird.

---

### Post by TheFu on 2022-01-22
Did you disconnect both external displays, then shutdown, wait 20 seconds, and boot with just the laptop, no external displays or keyboard or anything?
My laptop uses Fn+F3 to toggle between internal screen and different external screens. It is a BIOS/HW thing. There is a little image on the laptop keyboard.

The other stuff is probably a different issue, though they seem connected now.

So know which OS you are running, I'd ssh in from a different device and run **lsb_release -a**.  Tablet, phones, other computers can all ssh in, but that assumes you have ssh setup already.

The other thing to do is try using a different tty - <cnt><alt>+ F1 thru F8 ... try them and allow 5-10 seconds between hitting <enter> for the login screen to be displayed - on the primary display. When there aren't any external displays connected, this will be the laptop screen.

---

