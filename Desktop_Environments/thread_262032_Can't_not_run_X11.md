---
title: "Can't *not* run X11"
date: 2006-09-21
forum: Desktop Environments
---

### Post by Ububurns on 2006-09-21
A bit of an unusual problem, I admit - 

If I'm not running X, my LCD screen goes blank.

ie: I can't use the text-only terminals, or start up in a text-only mode.

This is proving to be an annoying problem, because if anything happens and X can no longer start, I'm stuck with a black screen.

Any help would be great!

---

### Post by ayoli on 2006-09-21
```
sudo aptitude install sysv-rc-conf
sudo sysv-rc-conf
```
uncheck the gdm in column 2.
reboot, you will be in text mode.
when you want X again do:
```
sudo sysv-rc-conf
```
and check the gdm line in column 2

---

### Post by Ububurns on 2006-09-21
Thankyou for your suggestion, but the solution you proposed only stops X from starting up.

This does not address the issue of not being able to display anything in text mode.  

To describe it another way, it's like the screen resolution during text mode is too high, so it displays nothing at all.

Does anyone have any other ideas?

---

### Post by ayoli on 2006-09-21
try to change screen resolution in /boot/grub/menu.lst

found a line looking like this:
```
defoptions=quiet splash
```
and try to change resolution by adding to this line:
```
vga=791
```
791 is mine (1024x768, 16bits ), here's a list of others:
```

	   640x480 	   800x600 	  1024x768 	 1280x1024
8 bits 	 vga=769 	 vga=771 	 vga=773 	 vga=775
16 bits vga=785 	vga=788 	vga=791 	vga=794
32 bits vga=786 	vga=789 	vga=792 	vga=795
```

---

