---
title: "how to change screen resolution?"
date: 2009-01-23
forum: General Help
---

### Post by YigalB on 2009-01-23
I installed new pc with Nvidia FX5200 card.
No matter what I tried - the resolution is limited to 640*480.
I activated the recommended Nvidia driver, but I cant locate how to tell the driver the resolution I need.
I tried also telling the OS the name of the CRT I use (CTX 1720), but the "hardware drivers" is showing only the NVIDIA card.

Any advise?

Also, until solving that, how do i scroll up and down within windows that are larger than my physical screen? some times it's frustrating since I cant see the "OK" button - it's just outside the screen's view.

---

### Post by stalkingwolf on 2009-01-23
Try this substituting your adapter information.

```
8. Log on with your user account that you created during the install. Open up terminal and enter "sudo displayconfig-gtk" (without the speech marks). The terminal will ask for a password. Just put in the PASSWORD that you normally log on with your username with.

9. A dialog box will pop up. Select Graphics Card from top. Click the button where it says 'Driver'. A window will pop up. Select the button where it says 'Choose Driver by model'

10. Select 'trident' on the left list box. On the right list box select what type of trident card you have (In my case I had a CyberBlade)

11. Click OK. Then Click ok on the other dialog box. Then restart the computer. When you log back in you will have the right resolution with your laptop. Enjoy 


```

---

### Post by YigalB on 2009-01-23
```
8. Log on with your user account that you created during the install. Open up terminal and enter "sudo displayconfig-gtk" (without the speech marks). The terminal will ask for a password. 
```[/QUOTE]

I got error message when I tried the "sudo displayconfig-gtk"
It seems I dont have the displayconfig installed: "command not found".

---

### Post by 3rdalbum on 2009-01-23
stalkingwolf: The Screens and Graphics program is no longer available in Ubuntu.

You can move windows up and down by holding down Alt and dragging inside them.

If the "Screen Resolution" program (Preferences > Screen Resolution) doesn't give you any additional options for resolution, you will need to add them to the /etc/X11/xorg.conf file manually.

---

### Post by YigalB on 2009-01-23
1- What does it mean "The Screens and Graphics program is no longer available in Ubuntu"? I still have graphic card and screen attached to my systems. How am I suppose to manage them?

2- "You can move windows up and down by holding down Alt and dragging inside them." I tried and I couldnt push the window up, so the bottom of the window is still hidden from me.

3- I located the file /etc/X11/xorg.conf, but I didnt know how to edit it. How can i set there additional resolution?

---

