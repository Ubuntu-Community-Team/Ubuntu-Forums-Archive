---
title: "LightDM and NumLock"
date: 2011-08-16
forum: Desktop Environments
---

### Post by crking on 2011-08-16
Before lightdm I used GDM and for my numlock being on every time i boot. i would 
put this:
if [ -x /usr/bin/numlockx ]; then       /usr/bin/numlockx on fi

in
/etc/gdm/Init/Default


how could I do this kinda action with lightdm???

---

### Post by hype on 2011-09-04
Ouch, posted two weeks ago... and i have the same issue.
There are config files for lightdm in /etc/lightdm, but could'nt find anything interesting things, well that i could understand.
 Google is not very helpfull neither :(

---

### Post by hype on 2011-09-04
There's a - non helpfull - bug report here [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/835532](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/835532)

---

### Post by jaimefdml on 2011-10-15
Not only the numpad. When I was in Ubuntu <11.10, I used to configure my external display to have the correct resolution in this way: 

xrandr --newmode  "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1360x768_60.00
xrandr --output VGA1 --mode 1360x768

Now, I don't know where to paste this stuff!!
Please, help me with the new lightDM. Where is the etc/Init/lightDM/Default file???

---

### Post by trendzetter on 2011-10-18
[how2 enable numlock with lightdm]("https://answers.launchpad.net/lightdm/+question/173666")

---

