---
title: "Jaunty TERRIBLE GRAPHICS ERRORS with ATI Radeon X1200"
date: 2009-04-24
forum: General Help
---

### Post by gaalaaant on 2009-04-24
guys I really need help, all my notifications and everything are ruined... I am scared...I need someone to hold me.  Nah joking, but I seriously can't figure out what's wrong! It was fine before the upgrade.  I CAN'T EVEN USE THE TERMINAL!! It just shows up as yellow and see through.

---

### Post by gaalaaant on 2009-04-26
Even my terminal pops up in yellow partially.  HELP!

---

### Post by aaeellxx on 2009-06-24
use sudo nano /etc/apt/sources.list

&

add this line

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main

the key:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 8844C542

&

sudo apt-get update && sudo apt-get upgrade


it helps to get better the new graphics in ubuntu 9.04 with some cards that include the mine ait x1200

i repeat, only in ubuntu 9.04 becouse have the drivers now included "Vesa drivers"

if you have some troubles, use the terminal tty X (ctrl + alt + F(1,2,3,4,5,6)

and try to post the file xorg.conf that are in /etc/X11/xorg.conf (X11 is with "X" no with "x")

also you can fix the graphics when the grub load press key "esc" and load the kernel that says something like "safe mode" and then repair xserver

are experimental and they arent 100% safe, but try, to me it fixed just a part bcoz the screen was flicking 

good luck¡¡¡¡

---

