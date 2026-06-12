---
title: "external screen problems.. but other than that v.impressed"
date: 2007-06-20
forum: Dell  Ubuntu Support
---

### Post by TrevorRS on 2007-06-20
hi, first post in this scetion

i have a dell latitude d505 lapto and i am very impredded with ubuntu on it, it just works very well everything i have i have had no problems with.. except the printer but it rather new so drivers havent been released for it yet!

but my question is about the external screen!

how can i get the external screen to work, it works when i close the lid but that makes typing a problem!

anyone help?

Cheers
Trevor

---

### Post by angryfirelord on 2007-06-20
ok, maybe this will work.

Open up a terminal and type ```
gksudo /etc/X11/xorg.conf
```
Now, scroll down to where it says *Section "Device"*.

Before we do anything drastic, let's say your device section looks like this.
```
Section "Device"
Identifier "GeForce FX5200 "
Driver "nvidia"
VideoRam 131072
Option "RenderAccel" "true"
BusID "PCI:1:0:0"
EndSection
```
I want you to copy the whole thing and paste it right beneath it. Now, add Screen 0 to one and Screen 1 to the other. Therefore, it would look like this.
```
Section "Device"
Identifier "GeForce FX5200 "
Driver "nvidia"
VideoRam 131072
Option "RenderAccel" "true"
BusID "PCI:1:0:0"
**Screen 0**
EndSection

Section "Device"
Identifier "GeForce FX5200 "
Driver "nvidia"
VideoRam 131072
Option "RenderAccel" "true"
BusID "PCI:1:0:0"
**Screen 1**
EndSection
```
If that fails, then hook up the external monitor and load the LiveCD. You can then look at the xorg.conf from there and compare it to the existing one.

---

### Post by TrevorRS on 2007-06-23
when i type in

gksudo /etc/X11/xorg.conf

nothing comes up or happens?

thanks for the help thought!


Trevor

---

### Post by scarboni on 2007-06-23
Try this instead: 
 
[PHP]1. Hit ALT-F2
2. Type in gksudo gedit /etc/X11/xorg.conf
3. Hit "Enter" or click "ok"
4. Follow the instructions above for adding screen information to xorg.conf[/PHP]
 
Let us know how it went.

---

### Post by TrevorRS on 2007-06-23
thansk for youre help!

i managed to fix it myself! youre way didnt fix it but if i press Fn and F8 it sayts crt/lcd beneath it but it seems to change the screen from internal to external!

Cheers

---

### Post by Tethtibis on 2007-06-26
i have a dell d505, preimbedded in the motherboard is the command, when you press the blue Fn key and F8, it goes to external monitore, same as Fn amd page up or page down doing volume, FN cursor up or cursor down doing screen brightness, Fn and F2 turns wireless off and on,  FN and esc suspends the comp, and SOO many more, just look for the blue wrighting on your keyboard. and, if you're using an external monitor, why not just close the lid and use an external mouse and keyboard? heh , the double vision would give me a headache.

---

