---
title: "Touchpad configuration/ acceleration"
date: 2021-10-13
forum: Desktop Environments
---

### Post by thomasg62 on 2021-10-13
[COLOR=#000000]Hi - firstly apologies if this is in the wrong place. It initially seems 'hardware' to me because it is about my touchpad, but I I got no replies there and so appreciate that it might actually be software.[/COLOR]

[COLOR=#000000]I am keen to install Ubuntu on my HP Elite X2 1012 G2, and have done so many time successfully on other laptops/ Pc's. However, when I do I cannot seem to get it to recognise my touchpad (this model has a detachable keyboard, if that's relevant). I get the setting for mouse, but not touchpad. Problem is that the touchpad works but is painfully slow to move the cursor across the screen. Adjusting the mouse settings does nothing to the touchpad speed. I need to accelerate it somehow, and have tried searching this but with no real success. I wouldn't have come on to ask this if I was really experienced and it was easy to find, so sorry if it is obvious to others.[/COLOR]
[COLOR=#000000]I have tried other Distros to see if this was a characteristic of main Ubuntu, but POP_OS, Zorin etc., all derivatives of course, were the same. Then I tried Elementary OS and the touchpad setting were there and worked great. I might have settled for that but it is as buggy as hell. Odin I think it is called. So many broken dependencies I cannot fix etc.[/COLOR]

[COLOR=#000000]Given that Elementary OS is again a derivative of Ubuntu it seemed plausible that I should be able to get proper Ubuntu to work. The touchpad is a deal-breaker for me. Can anyone assist?[/COLOR]

---

### Post by T6&amp;sfpER35% on 2021-10-13
if you go to settings - mouse and touchpad , can you see a box with **device** ? there should be an drop down arrow to choose the device.
you say the touchpad is slow , but at least it's being recognized otherwise it wouldn't have worked.

---

### Post by thomasg62 on 2021-10-13
Thanks for your response. In retrospect I agree that it has been recognised, ort it wouldn't work at all. Fair point. I'm guessing that with Xubuntu there is the drop down box illustrated, but it doesn't appear on regular Ubuntu 20.04, or its derivatives. Only the mouse settings are there. It's as if it sees it as a mouse, but adjusting the mouse configuration doesn't impact on the speed. I need about three swipes to get the cursor from one end of the screen to another. It's hopeless. Is there some terminal commands to make some adjustments? - if laid out for me i can follow these

---

### Post by thomasg62 on 2021-10-13
so, from another source I have identified that I have an ALPS driven touchpad, and it seems to be difficult to set up. Does anyone know how to do this?

---

### Post by ActionParsnip on 2021-10-13
Try
```

sudo lshw

```
in both OSes and note the differences for the touchpad device...

---

### Post by grahammechanical on 2021-10-13
In one sense Elementary OS is a derivative of Ubuntu but in other senses it is nothing like Ubuntu. The big difference is the Desktop Environment and the User Interface. It is the User Interface in Elementary OS that is giving satisfaction in this particular case in comparison to the Gnome3 Desktop Environment and Gnome3 Shell User Interface of Ubuntu. For this reason it does not follow that what works in the Elementary UI must of necessity also work in the Gnome UI.

Regards

---

