---
title: "Xbox360 xboxdvr"
date: 2014-08-14
forum: Gaming &amp; Leisure
---

### Post by db23 on 2014-08-14
I am trying to configure a wired, usb xbox360 controller on my acer revo3610, running ubuntu 14.04. 

I installed xboxdrv, but when I try to run it from xterm, I get error messages. It begins to initialize, then gives me a libusb_error_busy and suggests I rmmod xpad (I have blacklisted xpad per another instructional website). When I rmmod xpad, it says it isn't loaded.
The other option is to sudo xboxdrv with --detach-kernel-driver. When I do this, I get an error, libusb_error_not_found.
I'm able to run jstest-gtk and it shows 4 profiles. But none of them seem to be linked (or respond to) the xbox controller. Any suggestions? Thanks for the help.

---

### Post by hoodbrothers2 on 2014-08-14
Have you tried it without installing anything?  My xbox controller worked and I didnt have to do anything.  I'm even using a wireless.

---

### Post by db23 on 2014-08-14
I have tried using it with nes and snes emulators. Nothing so far. The middle button blinks for a bit and then has one continuously lit green light, but none of the controls seem to be recognized.

---

### Post by db23 on 2014-08-14
I am still struggling to get the xbox controller to work on ubuntu 14.04. So far I have installed xboxdrv and blacklisted xpad. When I try to run xboxdrv, I get a libusb error busy. I try to rmmod xpad, but it says it isn't currently loaded. Detach-kernel-driver just gives a different libusb error. I typically have a wireless mouse, external hd and a keyboard plugged into other USB ports. I remove all but the keyboard to run this. I have noticed that if I switch USB ports, all 4 lights will flash on the xbox controller. If I run xboxdrv, it works and says it should be module js0. When I run jstest-gtk, there is no js0 (only 1-4, none of which respond to the controller). When I exit that and run xboxdrv again, I'm back to the same libusb error busy message. Any ideas? Thanks.

---

### Post by db23 on 2014-08-15
I am still struggling to get the xbox controller to work on ubuntu 14.04 for my acer revo3610. So far I have installed xboxdrv and blacklisted xpad. When I try to run xboxdrv, I get a libusb error busy. I try to rmmod xpad, but it says it isn't currently loaded. Detach-kernel-driver just gives a different libusb error. I typically have a wireless mouse, external hd and a keyboard plugged into other USB ports. I remove all but the keyboard to run this. I have noticed that if I switch USB ports, all 4 lights will flash on the xbox controller. If I run xboxdrv, it works and says it should be module js0. When I run jstest-gtk, there is no js0 (only 1-4, none of which respond to the controller). When I exit that and run xboxdrv again, I'm back to the same libusb error busy message. Any ideas? Thanks.

---

### Post by QIII on 2014-08-15
Several threads merged.  

Please do not start multiple threads on the same subject -- and it is best if continuations of a previous thread are kept in the original thread.

---

### Post by dannyboy79 on 2014-08-16
i use the default xpad driver for my wired xbox 360 controller. i wrote this up, have a read: [http://ubuntuaddicted.blogspot.com/2013/11/xbox-360-controller-and-steam-games.html](http://ubuntuaddicted.blogspot.com/2013/11/xbox-360-controller-and-steam-games.html)

i believe it also has to do with the world readable permissions on the device node as well.

---

