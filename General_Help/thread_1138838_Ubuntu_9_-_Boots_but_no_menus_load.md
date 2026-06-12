---
title: "Ubuntu 9 - Boots but no menus load"
date: 2009-04-26
forum: General Help
---

### Post by iziizi on 2009-04-26
Hi,

So this is my first time ever using Linux, and was enjoying my experiance untill Ubuntu crashed. It crashed and didnt reload my menus, just the desktop and mouse. The 'start menu' and the application bar at the bottom do not show after reboot.

I think this happened when i was trying to install a remote desktop piece of software, but honestly cant remember as I was frantically doing several things in my new haste to learn the new OS!

Can anyone help with how I can recover my desktop? 

Many thanks for any help.

Iz.

---

### Post by perrti-y02 on 2009-04-26
If you press alt+f2 then type into the box you see gnome-panel this should reload your taskbars.

---

### Post by iziizi on 2009-04-26
> **perrti-y02 said:**
> If you press alt+f2 then type into the box you see gnome-panel this should reload your taskbars.

i just tried that and nothing happened? could my keybord not be loading?

---

### Post by todak on 2009-04-26
Same thing happened to my wife's computer. I tried to reconfigure xserver-xorg via a terminal. To my surprise, I was greeted with the response that xserver-xorg was not installed. So, I ```
sudo apt-get install xserver-xorg
``` and after everything was installed, I reboot and everything works fine.

---

### Post by iziizi on 2009-04-26
> **todak said:**
> Same thing happened to my wife's computer. I tried to reconfigure xserver-xorg via a terminal. To my surprise, I was greeted with the response that xserver-xorg was not installed. So, I ```
sudo apt-get install xserver-xorg
``` and after everything was installed, I reboot and everything works fine.

thanks for the reply, but sorry complete noob here :)

shall i boot in to safe mode? how do I get to the terminal window if I cant access anything?

---

### Post by todak on 2009-04-26
Yes, boot into safe mode and then choose root terminal with networking and then type the command I gave you, except do not use the word sudo. Just ```
apt-get install xserver-xorg
``` since you are in a root terminal already, you do not need root preiveleges to be root.

---

### Post by iziizi on 2009-04-26
> **todak said:**
> Yes, boot into safe mode and then choose root terminal with networking and then type the command I gave you, except do not use the word sudo. Just ```
apt-get install xserver-xorg
``` since you are in a root terminal already, you do not need root preiveleges to be root.


thanks for that, tried it and hasnt helped...

i might just re-install the whole thing unless there are any other suggestions?

---

### Post by todak on 2009-04-26
You can also try ```
sudo apt-get install ubuntu-desktop
```. and see if that works.

---

### Post by iziizi on 2009-04-26
> **todak said:**
> You can also try ```
sudo apt-get install ubuntu-desktop
```. and see if that works.

that hasnt helped either. i think i am just going to re-install, thanks for your help all the same

---

