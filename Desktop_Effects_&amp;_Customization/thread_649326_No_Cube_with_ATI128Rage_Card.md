---
title: "No Cube with ATI128Rage Card"
date: 2007-12-24
forum: Desktop Effects &amp; Customization
---

### Post by BITstate on 2007-12-24
:confused:I can not get the desk top effects working, I have a ATI 128 rage graphics card. I can not get any of the graphics to work at all.  I have the extended graphics window and can select the cube from the menu choices, but, I can not get the cube to work at all.  My machine is a AMD 1000Mhz, with 512Mb memory, and the above mentioned Graphic card.
I am new to Linux, ubuntu7.10 is my first install, so please keep any help offered simple.

---

### Post by Afkpuz on 2007-12-24
Well, here is a checklist to work through.  

1.) Do you have the current driver for your video card?
To check: System>Administration>Restricted Drivers Manager
Make sure that the little box next to your video card is checked and installed

2.) Is xgl-server installed?
To check: Goto a terminal Applications>Accessories>Terminal and enter this line
```
sudo apt-get install xserver-xgl
sudo apt-get install compizconfig-settings-manager
```

3.) After all that, are effects turned on?
To check: After doing the above System>Preferences>Advanced Desktop Effects

Hope this helps

---

### Post by Forlong on 2007-12-26
If it still doesn't work then, post the output of ```
compiz
``` in a terminal.

---

### Post by BITstate on 2007-12-26
johnus@johnus-desktop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

:confused: SOS!!!...

---

### Post by Forlong on 2007-12-26
I did some research on your graphics card and I'm afraid Compiz (or any other desktop effects) won't run with it.
It's too old, so ATi doesn't have any driver for that card that provides non-power-of-two texture support.


Edit: if you followed Afkpuz' advice, make sure to remove Xgl again:
```
sudo apt-get remove xserver-xgl
```

---

### Post by BITstate on 2007-12-26
ForLong

Thank you for researching the ATI problem, I have deleted the xserver-xgl as you said.

If I were to replace this aging graphics card, what would be a good replacement?,
I don't want to buy another card and find that it is not supported by ubuntu 7.10.

Thank you to everyone that has posted advice on this Thread\\:D/

BITstate

---

### Post by Forlong on 2007-12-26
Definitely go with a Nvidia, if you want to use desktop effects. ATi's support for Linux has been very disappointing to this day in this respect.

Other than that, any contemporary card should do.
I can't recommend any specific model, though. You might want to ask that in the hardware section of the forum.

---

