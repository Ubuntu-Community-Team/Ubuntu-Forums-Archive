---
title: "Funky mouse problem..."
date: 2007-02-13
forum: Desktop Environments
---

### Post by grantjohnston on 2007-02-13
Alright, I'm not sure if you guys have **EVER** run into this problem before. I'm running Xubuntu Edgy on a 64bit AMD 3800 using a Logitech MX1000. Everything works peachy, until I reboot the machine. Then, X won't load and I get a No core pointer error. That's with it looking for the mouse on PS/2 and it still plugged into the PS/2 port. So, I shutdown the machine, plug the mouse into a USB port, and turn it back on. Still get the error No core pointer (obviously). However, if I then plug the mouse into the PS/2 port, bam, X starts and works perfectly. I'm not sure if this makes any sense, if you need more info, let me know. This is driving me insane having to do this everytime I wind up restarting.

Also when it boots with it being plugged into the PS/2 port and I get No Core Pointer. I can go into xorg.conf and change it to look on the USB port (after putting it into one) and X will start, but all the buttons are screwy (back, forward, scroll, etc.).


Any input is appreciated


Thanks


Grant

---

### Post by dcstar on 2007-02-13
> **grantjohnston said:**
> Alright, I'm not sure if you guys have **EVER** run into this problem before. I'm running Xubuntu Edgy on a 64bit AMD 3800 using a Logitech MX1000. Everything works peachy, until I reboot the machine. Then, X won't load and I get a No core pointer error. That's with it looking for the mouse on PS/2 and it still plugged into the PS/2 port. So, I shutdown the machine, plug the mouse into a USB port, and turn it back on. Still get the error No core pointer (obviously). However, if I then plug the mouse into the PS/2 port, bam, X starts and works perfectly. I'm not sure if this makes any sense, if you need more info, let me know. This is driving me insane having to do this everytime I wind up restarting.

Also when it boots with it being plugged into the PS/2 port and I get No Core Pointer. I can go into xorg.conf and change it to look on the USB port (after putting it into one) and X will start, but all the buttons are screwy (back, forward, scroll, etc.).


Any input is appreciated


Thanks


Grant

I would leave the mouse in a USB port and then do in a terminal:
```
**sudo dpkg-reconfigure xserver-xorg**
``` and see if things are more stable after a reboot.

---

### Post by grantjohnston on 2007-02-14
> **dcstar said:**
> I would leave the mouse in a USB port and then do in a terminal:
```
**sudo dpkg-reconfigure xserver-xorg**
``` and see if things are more stable after a reboot.

I'm at class right now, but I will try that as soon as I get home. The only problem with putting it in a USB port, is that all the buttons are screwy.. Or, should that command fix the button problem?



Cheers

Grant

---

### Post by mgmiller on 2007-02-14
Try looking in your BIOS and see if you have the PS2 mouse option (if available) turned on.  Also look for an entry like USB legacy support and if it's on, turn it off or if it's off, turn it on.

---

### Post by grantjohnston on 2007-02-14
> **dcstar said:**
> I would leave the mouse in a USB port and then do in a terminal:
```
**sudo dpkg-reconfigure xserver-xorg**
``` and see if things are more stable after a reboot.

Hmm, that seemed to work, kind of... I restarted once, and now the mouse doesn't work, but, hey, X actually starts now... However, I didn't have any of my video settings saved, so now I have to redo all of that :doh:. And all the buttons for the mouse.. :(


> **mgmiller said:**
> Try looking in your BIOS and see if you have the PS2 mouse option (if available) turned on.  Also look for an entry like USB legacy support and if it's on, turn it off or if it's off, turn it on.

Tried that first.. Didn't work.

---

### Post by grantjohnston on 2007-02-14
After finding a 5 month old xorg.conf sitting around, I got Beryl workin again, and the mouse.. However, it seems that the keys are confused, when I scroll up, it's acting like I'm clicking back on the mouse, when I scroll down, going forward. I guess the keys are backwards. I'm going to try and change some of them and see if I can't get them all working again.. This friggin' thing is driving me batty.

---

### Post by grantjohnston on 2007-02-14
After following the guide to the MX1000, I'm still nowhere, I Had the keys working properly. I restarted and it tanked and they're back to their normal FUBAR ways.. Any ideas appreciated



Thanks



Grant

---

