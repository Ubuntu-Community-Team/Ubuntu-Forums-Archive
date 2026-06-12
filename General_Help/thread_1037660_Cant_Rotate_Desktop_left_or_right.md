---
title: "Cant Rotate Desktop left or right"
date: 2009-01-12
forum: General Help
---

### Post by rvasquez6089 on 2009-01-12
I have Nivdia 9800gtx and i am running Ubuntu 8.10. i would really like to rotate my desktop but i can't. I have already tried going to  System>Preferences>Screen Resolution and changing it. And i have tried typing in the command xrandr -o left, after i type that in i get  

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12
 
i need help!!!!!!! what do i do

---

### Post by gettinoriginal on 2009-01-12
I'm confused, are you talking about rotating as in the compiz cube ??  Or are you talking about rotating the screen as in edge to top ??

---

### Post by gettinoriginal on 2009-01-12
Just found this:
```
sudo gedit /etc/X11/xorg.conf
```

and added
Option "RandRRotation"
so it looks like this.

Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
Option "NoLogo" "true"
Option "RandRRotation"
EndSection


rebooted just for the effects to take place.

---

### Post by rvasquez6089 on 2009-01-12
Thanks dude !!!!!!!!!!!! i really appreciate!!!!!!!!! i guess i will eventually learn how to solve my own problem like i did in windows.:o

---

### Post by gettinoriginal on 2009-01-12
You are welcome, please go to thread tools and mark this as solved.  :P

---

