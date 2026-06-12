---
title: "ctrl+alt+F1=boom! (6.10)"
date: 2006-10-28
forum: Desktop Environments
---

### Post by dak-AD on 2006-10-28
hi. first off, im not too experienced with ubuntu/linux, so sorry if this is confusingly worded.

also, i tried to submit a bug, but because i dont really know what's supposed to be happening, i dont really know how to word the bug/check if it's already been submitted :confused: 

ok, basically if i try to switch to consol mode (am i right thinking that's the text-mode? like terminal, but full-screen?) by pressing ctrl+alt+F1, the top-left quater/third of my screen is displayed (ie, really large, like 640*480 res, but the whole screen can't fit on my monitor), and the computer freezes up -- i can see the cursor but not move it, and stuff like ctrl+alt+F7, ctrl+alt+<--, pressing the power button etc dont have any effect. ctrl+alt+del makes my PC go 'beep' but thats about it...

this also happens when closing down zsnes, which otherwize works fine.

anyhoo... 

i assume this isn't a universal bug, or someone would (i assume) have fixed it, so:

anyone know how to fix this? if not, can anyone help me word a bug report (what info is needed, etc)? 

cheers.

---

### Post by arctic on 2006-10-28
Sounds like a problem with the power management or I/O. Check your /var/log/messages and /var/log/dmesg file for errors. Is there something unusual reported? If yes, please post the output of it before submitting a bug. Maybe it is a trivial thing that needs to be adjusted. Post the error message and several lines before, too, because we need to know the context of the error.

---

### Post by dak-AD on 2006-10-28
thanks :)

i deleted the contents of messages and dmsg, so that any errors would be easy to find.

i tried ctrl+alt+F1, and seemed to have a case of remote technitian syndrome... it worked, and threw me to the consol ](*,) 

alt+F7 returned me to the desktop.

i managed to forse the error by running zsnes (usually not nessesary for the bug to happen), which made the screen 'go big'. alt+backspace rebooted the GUI shell(?). *then* alt+F1 made the screen 'go big' and lock up, and i had to unplug the pc.

rebooted, looked in the logs, and nothing jumps out at me as an error. do you want the entier logs posted?

ooh, one thing i just thought of: zsnes changes the screen resolution -- if switching to consol does aswell (might make sence, kinda like a 'safe mode'), then it might be a problem in switching screen resolutions? i normally have 800*600 res, and can change it via preferences with no problem tho. :confused:

---

### Post by odelay on 2006-10-28
A similar thing happens to me.  ctrl+alt+F1-6 makes my screen go all technicolored and crazy, but I'm always alble to go back to ctrl+alt+F7 withouth any problems.  I have the proprietary ATI (8.29.16) drivers, and fglrxinfo gives me a proper response.

---

### Post by huwshimi on 2006-11-03
*Bump*

---

### Post by leonya on 2006-11-07
> A similar thing happens to me. ctrl+alt+F1-6 makes my screen go all 
> technicolored and crazy, but I'm always alble to go back to ctrl+alt+F7 
> withouth any problems. I have the proprietary ATI (8.29.16) drivers, and 
> fglrxinfo gives me a proper response.

 Exact same problem here. I have ThinkPad T60 with ATI.

---

### Post by wish on 2006-11-09
same here, thinkpad t60p

---

### Post by hoodwink on 2006-11-11
Erratic behavior when switching to a console(CTL-ALT-Fn) and back to gui mode (CTL-ALT-F7) is (almost) always a problem with the accelerated video driver (nVidia or ATI). On our systems at work (RHEL4 and HP boxes with ATI card), this operation frequently locks the box requiring a reboot.

Is there a later driver for your ATI card that you could try?

---

### Post by kerry_s on 2006-11-11
Try adding-> vga=normal to your menu.lst boot line, so it'll look  like this->

kernel  /boot/vmlinuz-2.6.17-10-386 root=/dev/hdd3 ro quiet splash vga=normal

---

### Post by odelay on 2006-11-12
I changed mine to this -->

/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single vga=normal

and it didn't fix anything.  Thanks for the help anyway.

---

### Post by junglepeanut on 2006-11-12
This is a long standing bug. It occurs from many different interactions mostly involving logout and hot-key restarts of x. It has many multiple listings, if I understand what you are talking about.


[https://launchpad.net/distros/ubuntu...ati/+bug/30447](https://launchpad.net/distros/ubuntu...ati/+bug/30447)

Some cures on this page...mine is still bottoms up.

I find ctrl+alt+bckspc works 50% of the time, otherwise I just 

sudo shutdown -r now

As Edgy made restarts very fast for me (less than thirty seconds to stop and less than thirty seconds to start concluding the start time with an open firefox google homepage.)

---

### Post by leonya on 2006-11-30
> **wish said:**
> same here, thinkpad t60p

On my thinkpad t60 I was able to fix the problem by removing the "splash" from the kernel boot parameters.
Just remove "splash" from everywhere it appears in /boot/grub/menu.lst
I can then switch to the terminal screens without any problem.

The bootup is not as pretty, but seems to be actually faster.

---

### Post by hoodwink on 2006-12-02
> **dak-AD said:**
> 

ok, basically if i try to switch to consol mode (am i right thinking that's the text-mode? like terminal, but full-screen?) by pressing ctrl+alt+F1, the top-left quater/third of my screen is displayed (ie, really large, like 640*480 res, but the whole screen can't fit on my monitor), and the computer freezes up -

this also happens when closing down zsnes, which otherwize works fine.


Sorry to come into this late, but ...

1. This is a univeral problem with ATI (~= CRAP) video cards and their sucky Linux drivers. I personally wouldn't touch a PC with ATI video. Unfortunately we have to put up with this at work (very similar results to yours).

2. Maybe you can find a later ATI driver that fixesthe problem?

3. Maybe AMD will clean out the stables nowthat they own ATI.

Good luck,

---

### Post by apalacheno on 2006-12-07
I hope so. Same problem here on a ThinkPad Z61m with ATI's X1400 card.

---

