---
title: "keyboard setup help"
date: 2008-12-23
forum: General Help
---

### Post by proevofanatik on 2008-12-23
i think ive messed up my keyboard settings. i dont know whats caused it. but when i go to try and reconfigure it  through system/ preferences / keyboard i get this error message.

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10502000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

why am i getting this?

i cant get the pound sign, # and @ are in wrong place.

please help

---

### Post by proevofanatik on 2008-12-23
i am trying to edit my xorg.conf file but it wont let me save it. it says
Could not save the file /etc/X11/xorg.conf.

You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.

what am i doing wrong?

---

### Post by proevofanatik on 2008-12-23
please someone help. i need to get a letter typed up asap. and it needs the pound sign in it.

---

### Post by thestig_992 on 2008-12-23
you need root permissions to edit the file, but be very careful doing that, as you could very easily compromise your system. If you dont know exactly what youre doing i wouldnt touch the file

---

### Post by proevofanatik on 2008-12-23
so how would i get my keyboard settings back to normal?

---

### Post by Wickd on 2008-12-23
If you need to type a letter urgently just use the character set in Open Office to get the punds sign. What are you trying to change in your Xorg.conf file?

---

### Post by proevofanatik on 2008-12-23
i think i might have something to do with setting my joypad to act as a mouse. i had toy edit the xorg.conf file to do this. it was only when i turned pc on this morning i went to type and found some of my keys were messed up. so i did a bit of searching and found that some people added some data into the xorg file to set the language layout of the keyboard. but when i try and do that i get the following error. 

Could not save the file /etc/X11/xorg.conf.

You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.

---

