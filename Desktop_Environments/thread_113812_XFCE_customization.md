---
title: "XFCE customization"
date: 2006-01-07
forum: Desktop Environments
---

### Post by prizrak on 2006-01-07
Is there a way to make the XFCE taskbar more like gnome panel? The thing I would like to do (at minimum) is have a clock, a wi-fi monitor, a sound control (highly optional), and the battery monitor. XFCE panel has all of those but it is on top and autohides which makes alot of those things not as convenient, and this being a laptop screen real estate is precious. I'm not afraid of CLI or installing a 3rd party taskbar/panel that can be customized more, also if it is possible to make the gnome panel replacement desklet stay always on top like the regular panel does that would work as well.

---

### Post by kairu0 on 2006-01-07
1. You can kill the taskbar, add a taskbar to the XFCE panel, move the panel to the bottom, and turn off autohide.

2. There is xfce4-iconbox, which can be moved to any part of the screen and works as a taskbar without labels.

There is a patch to move the systray from the right to the left side of the taskbar, but that's about as much as you can customize the taskbar.

---

### Post by prizrak on 2006-01-09
LOL it's kinda funny, but that is EXACTLY what I did before reading your post. There is also a windowlist plug in for the panel as well as systray plug in.
I got another question now tho. How do I set things to autostart on XFCE start I need devilspie and gdesklets to start up and "Save session" doesn't do it for some reason.

---

### Post by DaMasta on 2006-01-09
Create a folder in Desktop called Autostart and link from there.

---

### Post by prizrak on 2006-01-10
[QUOTE=DaMasta]Create a folder in Desktop called Autostart and link from there.[/QUOTE]
Where do I put the link into?

---

### Post by prizrak on 2006-01-11
NM I gave up on XFCE once it refused to auto mount my USB Flash drive. Now it's Gnome with XFWM runs almost as fast but I still get weird font distortion that I always did :(

---

### Post by Zelut on 2006-01-16
I've been playing with XFce and really enjoy how lightweight it is but I also need access to my usb drive and, sadly, have no idea how to mount that manually.  I really like how it works in gnome (icon pop-up on the desktop).

Any tips or suggestions?

---

### Post by simon_is_learning on 2006-01-17
plug in the usb stick. here is the command i would use assuming you have only one usb storage device.

sudo mkdir /mnt/usb_stick
sudo mount -t vfat /dev/sda1 /mnt/usb_stick

if that doesnt work then paste in the last 30 lines of running 'dmesg' for us to see. 


I found that in another Forum, Tough I haven't managed to make it work so that if I unplugg the stick and then put it back it appears again. 

Maybee you will have better luck

---

### Post by simon_is_learning on 2006-01-17
plug in the usb stick. here is the command i would use assuming you have only one usb storage device.

sudo mkdir /mnt/usb_stick
sudo mount -t vfat /dev/sda1 /mnt/usb_stick

if that doesnt work then paste in the last 30 lines of running 'dmesg' for us to see. 


I found that in another Forum, Tough I haven't managed to make it work so that if I unplugg the stick and then put it back it appears again. 

Maybe you will have better luck

---

### Post by kaamos on 2006-01-17
You can run ivman or gnome-volume-manager with xfce to manage automounting. Just start either and remember to save your session.

---

