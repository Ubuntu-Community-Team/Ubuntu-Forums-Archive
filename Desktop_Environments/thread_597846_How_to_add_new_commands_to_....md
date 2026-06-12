---
title: "How to add new commands to ..."
date: 2007-10-30
forum: Desktop Environments
---

### Post by jgag123 on 2007-10-30
Hi everyone.

I am new to ubuntu, using festy for two months but did not try working with the terminal yet.

I was going to add command to an existing ones but i don't know how to do it.

Trying to follow an instruction that I found on a forum:  Add the following lines to /etc/modprobe.d/blacklist

blacklist rt73usb

blacklist rt2570

I can open the /etc/modprobe.d/blacklist, but when I type the blacklist rt73usb and

blacklist rt2570 commands in there how to save it and close it.

Any help would be appreciated

---

### Post by brownknight on 2007-10-30
Hi

You can use "nano" to edit so just type

sudo nano /etc/modprobe.d/blacklist

it will ask for your sudo password

then add what you wanted to edit

blacklist rt73usb

blacklist rt2570

then press ctrl+o (to overwrite/save the file)
then press ctrl+x (to close)

your done :)

---

### Post by Prospero2006 on 2007-10-31
The pico text editor is also easy to use.

---

### Post by dukejib on 2007-10-31
Gedit is as good as nano or pico, in addition, the guy is a newbie, so gedit is safe bet.

---

