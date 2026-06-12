---
title: "Labview and graphic problem"
date: 2009-05-31
forum: General Help
---

### Post by WeEnterWinter on 2009-05-31
I successfully installed labview on my ubuntu 9.04, and it works fine, but I found a tiresome problem using the "block diagram". When I move the window or when I pass the cursor over the window some graphic problems occur: the colors change and some elements just disapper. I post a screenshot so you can understand.
The kernel version is 2.6.28-11. I have a video card  Intel GM965  and the driver is intel 2.4.

[IMG]http://www.allfreeportal.com/imghost/images/690946Immagine.png[/IMG]

---

### Post by Thelasko on 2009-05-31
Did you try setting visual effects to "none"?

System>Preferences>Appearance>Visual Effects

---

### Post by WeEnterWinter on 2009-06-01
I tried. Same result unfortunatly...

Other ideas?

---

### Post by Thelasko on 2009-06-03
Well, you could try to see if there are different graphics settings in LabView.  If that doesn't work, you could try to use the graphics drivers from 8.04.  They tend to be more stable.

---

### Post by alexandre_bastien on 2009-06-20
I have the same problem. Let me know if you find a workaround for this.

---

### Post by prelution on 2009-08-17
[FONT=Arial][SIZE=2][COLOR=black]http://ubuntutip.googlepages.com/bugsinubuntu

In this posting it states a way to get rid of that problem.

just type in the terminal:

> [/COLOR][/SIZE][/FONT][SIZE=4][COLOR=#3333FF][FONT=Arial][SIZE=2][COLOR=black]apt-get remove xserver-xorg-video-intel
[/COLOR][/SIZE][/FONT][SIZE=2][FONT=Arial][COLOR=Black]> reboot

This will revert back to the 810 intel video driver that does not suffer the same problem.  However, I can't change my resolution to something better but that moot if I cant use labview.

Prelution
[/COLOR][/FONT][/SIZE][/COLOR][/SIZE]

---

