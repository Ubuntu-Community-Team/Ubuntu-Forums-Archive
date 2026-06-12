---
title: "LogiTech Keyboard functions"
date: 2006-06-18
forum: Desktop Environments
---

### Post by racsw on 2006-06-18
Hi,
  I just installed a new wireless LogiTech MX3000 Laser Keyboard and mouse, and they work very well with Umbutu.

This keyboard has quite a few special function buttons, like "Email", "My Documents", "Messenger", "Media", etc, etc, that activate an application with a single button.
As everything else on the keyboard works, I'm hopeful there is some way I can program these special keys in Umbutu.

Any procedures available for this?

Thanks,
Robert

---

### Post by JW_00000 on 2006-08-08
You may want to try [KeyTouch]("http://keytouch.sourceforge.net/"), an application to configure these special keys. I have heard that the profile for the MX3100 would work on the MX3000 too, but can't confirm it. Anyway, it would be great if you could write back your experiences with this keyboard, because I'm thinking about buying one too.

---

### Post by bboop on 2006-08-08
I use a Logitech Cordless Keyboard (Y-RE20) w/ Dapper (KDE)  with KeyTouch 2.1 and it is great!:D

---

### Post by JW_00000 on 2006-08-28
I now bought one of these keyboards, the Logitech MX3000, but only some special keys are working because I had to connect the keyboard to a USB port (I don't have a PS/2 port). The KeyTouch website reports the following on this issue:
> USB keyboards

When your keyboard is connected via USB you may have noticed that some extra function keys don't work. Note that most keyboard files in keyTouch are for a PS/2 connection and if a keyboard file is for a USB connection the name of the keyboard file will contain "(USB)". But still even if you are using the right keyboard file, some keys may not work. This is because the current USB input driver in the Linux kernel does not allow us to get these keys working. Currently I am modifying this driver so that we can get all keys working. This modification will be applied to the Linux kernel.

So at the moment I recommend you to connect your keyboard via PS/2 and wait for a new version of the USB input driver. I will also write a new version of keyTouch that will work perfectly together with the new driver. 

---

### Post by bihe on 2006-11-02
The ubuntu community is just great. You really find an answer for almost everything. Now the multimedia buttons of my keyboard work !

thanx

---

