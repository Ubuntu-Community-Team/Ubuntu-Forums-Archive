---
title: "PSX to USB Adaptor will not work"
date: 2006-08-24
forum: Desktop Environments
---

### Post by feerie on 2006-08-24
I have a PSX/N64 to USB Adaptor. After scouring the net for quite a while, I've found that it's called the "Boom PSX/N64 to USB Adpator" On the back the model number is XK-PC2004. It works fine in Windows XP SP2 without any drivers...but i've completely switched to Ubuntu, and I want to play some PSX games!

However, when I plug in the adaptor, it certainly doesnt register a joystick anywhere. Dmesg informs me :
 hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?

No matter which USB port I plug it into, front panel or on the back.

my USB Keyboard and Mouse are working fine so theres no issues there. 

This is on Dapper 6.06 , amd-64 edition. Kernel is 2.6.15.26. 

joydev and gameport modules are loaded.

Anyone have any ideas, before I have to either buy some crappy USB Gamepad thats a pale imitation of a PSX controller, or a different adaptor? This particular one has been reported to work in Linux, but with these sort of odd devices maybe its hit or miss.

---

### Post by Baraclese on 2007-12-22
Hi, this problem persists with Gutsy. It recognizes the two analog sticks on my DualShock Controller but no buttons, except for the analog/start/select and stick buttons.
I found this somewhat old page [http://www.elbionico.com/docs/usbjoy.html]("http://www.elbionico.com/docs/usbjoy.html") which says

"I have heard from several people that the vanilla uhci.o module does not work. The solution seems to be to use the usb-uhci module instead of the uhci module. To find out what module you are using, run the lsmod command. If you see plain uhci listed, try executing (as root) the commands "rmmod uhci" then "insmod usb-uhci". Keep in mind that the rmmond will stop any USB devices that you have running, including the keyboard. Everything should start running again when the usb-uchi module is inserted."

I don't know how that translates to today and Ubuntu though.

What can I do?

---

### Post by Baraclese on 2007-12-24
I've played around a bit more and found that the issue seems to lie somewhere else, as both WinXP SP2 and Gutsy show the same behavior with my DualShock PSX pad. The N64 Controller port on the other hand works fine on both Operating Systems, so I'll just be using my N64 pad for now.

---

### Post by brennydoogles on 2008-01-23
So did you eventually get the N64 controller part of your adapter to work? I have a similar (if not the same) adapter, and I'm not sure how to get it working. Any help would be great!

---

