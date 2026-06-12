---
title: "Can't Login, Dead Keyboard Mouse"
date: 2009-04-19
forum: General Help
---

### Post by lxskllr on 2009-04-19
I got 9.04 installed with the alternate media, but I can't login. The keyboard and mouse work until I get to the login screen, then they both die. I had this problem in 8.10 also, but I could usually get in after performing a couple of hard resets. This technique hasn't worked with 9.04 :^/

I think I've scoured the forums for information, and while I've seen some with the same problem, I haven't been able to fix it. The only thing I've really tried, is adding these entries to xorg.conf...

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection


Section "ServerLayout"
Identifier "Default Layout"
screen "Default Screen"
Inputdevice "Generic Keyboard"
Inputdevice "Configured Mouse"
EndSection

I've tried both USB, and PS2 devices, and unplugging them, and plugging them back in has no effect. The other pertinent hardware is as follows...

Intel 865 mb (Asus P4P800SE)
P4 2.8
512mb ram
Albatron TI4200
HP DVD drive
120gb hd aprox 1/2 XP, 1/2 Jaunty EXT4 and swap

Any help you can provide will be greatly appreciated :^)

---

### Post by lxskllr on 2009-04-19
^^

Up, up, great day for up.

---

### Post by xthatrox on 2009-05-24
I've got the same problem.  I upgraded from Hardy to Intrepid and now the mouse and keyboard are not responsive at the login prompt (except I AM able to ctrl-alt-f1 to a console). 

Does anyone have a solution to this?  I've tried installing xserver-xorg-input-mouse, xserver-xorg-input-kbd, xserver-xorg-input-all
It certainly appears to be an X problem, which is solved when starting X as a logged in user.  The only way I've found to get around the problem is to ctrl-alt-f1 and then run 
 sudo killall Xorg
This restarts X and then the login screen comes up and the mouse and keyboard work perfectly.

Any insight would be greatly appreciated.  Thanks.

---

### Post by markosp on 2009-08-22
sudo apt-get install --reinstall xserver-xorg-core

that worked for me:)

---

