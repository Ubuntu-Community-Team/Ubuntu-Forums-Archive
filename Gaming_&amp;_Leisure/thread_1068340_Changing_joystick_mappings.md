---
title: "Changing joystick mappings"
date: 2009-02-12
forum: Gaming &amp; Leisure
---

### Post by cdahmedeh on 2009-02-12
Hello,

I have a Sixaxis controller. I noticed that the controller mappings are very strange and I would like to change them. For example, I would like switch button 1 with button 2 and axis 12 with axis 1. Is that possible ? Is there any GUI for such thing ? How about a script where I click a shortcut and it changes the mapping ? 

Thanks

---

### Post by cdahmedeh on 2009-03-02
Any help, I've tried a patched version of JsCal, but it dosen't work if you have more than 16 axis (which the sixaxis does because all the buttons are analogue).

---

### Post by cdahmedeh on 2009-03-05
Anyone willing to help ?

---

### Post by falkTX on 2009-03-05
I want to help, but I've no idea how to do that.
I'm actually trying to find a way to get sixaxis' motion sensors to work as joystick (all I got is terminal echo). The best way to do this is trough a fake joystick module, but I'm not sure if it exists

---

### Post by cdahmedeh on 2009-03-05
YAY finaly someone who replies... I'm not interested in the Sixaxis gyro function right now, just willing to switch some axis for better compability with games (ex. use analog part of trigger, its like axis 13, can't be read by most games). I'm guessing you used some hex dump of hidraw to get reading from the sensor or something. It seems that the joystick driver in Linux is very low level and very hard to work with. I remember in Windows there was this program called PPJoy that allowed you to create Virtual Joysticks and then use GlovePIE to input into that driver. Also, I'm guessing that the joystick device is created by the bluez-compat program rather than your sixaxis-gui program. 

Right now the problem is that the patched jscal (can be found by search in this forum) only supports switching joysticks with less than 16 axes. Anything more causes problems and it doesn't switch

---

### Post by TheHolm on 2009-03-05
xev application can show you what you joystik send to X.

For remapping you can try "pyrostromo". It works wonder for remaping devices simulating keyboards and mouses.
I'm personnaly use it to remap keys for Belkin Nostromo52te game controller  and some noname IR remote. But I hope it can hadle joystiks as well.
It does not have any GUI.

Updated: Just checked documentaion. pyrostromo can handle joysticks.

---

### Post by cdahmedeh on 2009-03-05
No I don't want to map a joystick button to a keyboard or mouse button. I want to switch axis. For example, lets say my right analog trigger uses axis-13. My game (Live for Speed in Wine) supports only 10 axis, so it cannot read axis-13. Now lets say I want to switch an unused axis (5-10 are unused in the sixaxis driver) to a another one. So I want to relocate axis 10 lets say to axis-4. Then it will readable by the program. 

So I can imagine two possible workarounds :
-Change the axis assignments in the Linux Kernel driver
-Change the axis assignments in Wine (is it possible ?)

Thanks

---

### Post by TheHolm on 2009-03-05
Pyrostromo can also remap joystik movements. 
So nothing preevent you to remap one axis to other.

It is writen on python so you can easaly modyfy it yourself.

---

### Post by cdahmedeh on 2009-03-05
Where can I get this Pyrostromo ? I search google and get 0 results. Nothing on this forum either...

---

### Post by cdahmedeh on 2009-03-05
SOLUTION FOUND !!!!!
It seems that the patched jscal supported a maximum of 16. So I decided to open the jscal.c file included in the patched version, and changed #define MAXAXES 16 to 32. After that, make clean, then make and it works !!!!

---

### Post by TheHolm on 2009-03-05
My apologies. I have spelled it wrong way. 

"pystromo"

[https://launchpad.net/pystromo](https://launchpad.net/pystromo)

---

### Post by Ted_Kazynski on 2010-12-26
how do i "make clean"? Ive used linux for over a year and still don't understand the make, config, or any of the terminal stuff. i don't know how to change directories either. I have the same controller and just want to map the buttons in no$gba for wine. I don't know what a branch or trunk is either. how do i use these things? I feel retarded.

---

