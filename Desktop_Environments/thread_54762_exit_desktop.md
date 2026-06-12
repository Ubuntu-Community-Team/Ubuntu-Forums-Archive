---
title: "exit desktop"
date: 2005-08-05
forum: Desktop Environments
---

### Post by richardspirit on 2005-08-05
I am trying install new graphics drivers but I have to exit the desktop gui first but I can't remember the command to exit gui and I can't find it anywhere. 

Can anyone help me?

---

### Post by jasmuz on 2005-08-05
Do the following

alt+ctrl+f1 (takes you to a terminal)

sudo init 1 (places you in maintanance mode)

and install your drivers then. 

then type 

init 5

And your back!

---

### Post by Omnios on 2005-08-05
Ctr/Alt/F1 
 
 sudo /etc/init.d/gdm stop =to stop

 sudo /etc/init.d/gdm start =to start

 what video card driver are you installing you may have to install linux-headers
 If its nividia there is a how to in the wiki.

 Edit: I have to stop looking things up posts seem to sneak in lol

---

### Post by richardspirit on 2005-08-06
Okay thanks, I got to the terminal

I am installing nvidia drivers

what does uname mean in this line?
sudo apt-get install build-essential linux-headers-`uname -r`

---

### Post by jasmuz on 2005-08-06
uname -r (you run it in your terminal and it will tell you the current version numbering for the kernel that you are running)

---

### Post by richardspirit on 2005-08-06
oops

somehow I caused gnome to stop working. I'm not good enough yet of working without a gui, so I had to reinstall the whole thing.

Oh well, I guess it makes for more experiance.

---

