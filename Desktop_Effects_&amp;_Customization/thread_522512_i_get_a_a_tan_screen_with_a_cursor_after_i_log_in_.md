---
title: "i get a a tan screen with a cursor after i log in reboot after i installed compiz"
date: 2007-08-10
forum: Desktop Effects &amp; Customization
---

### Post by sirab on 2007-08-10
I have a toshiba a105 s4254 nvidia go 7300 or 7600 graphics card with an intel core 2 chip

I have the latest drivers for it 

i installed compiz fusion enabled it... but when i reboot i get the normal log in screen.. i log in.. adn all i get is a tan screen with a cursor 

im running gnome if it matters

this happened the last time i installed compiz and i had to reinstall linux

i installed compiz on my fresh install and now im scared to reboot hahah

i want to fix everything before everything goes wrong.

---

### Post by kansei on 2007-08-10
Does pressing Alt+F2 bring up the run dialog still? if it does, try "compiz --replace"

---

### Post by dannyboy79 on 2007-08-10
this happened to me when I installed Gutsy Tribe 3 on my Dell Dimensio 8200 with an Nvidia MX 440. I could do alt-F2 and type in compiz --replace only sometimes, otherwise I had to hit ctrl-alt-f1, login on tty1, then do a ps aux | grep compiz, I had to kill them all, then stop gdm, then start gdm and then there was my desktop. Then I had to update my xorg.conf to have Composite at the end of that file along with these common settings.
Option         "RenderAccel" "true"
Option         "AllowGLXWithComposite" "true"
under the device section and then these 2 under the screen section
Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"
then save xorg.conf, tehn do a ctrl-alt-backspace and your compiz should be working with the desktop coming fully in instead of getting stuck like it did. good luck

---

