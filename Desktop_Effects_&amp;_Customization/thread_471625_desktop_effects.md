---
title: "desktop effects"
date: 2007-06-12
forum: Desktop Effects &amp; Customization
---

### Post by yousufinternet on 2007-06-12
hello every body 
i have installed ubuntu 7.04 on my desktop and i realy enjoy it and i distributed a copies of the cds to my friends here in Jordan ....
my question is : when i try to run the desktop effects System>preferences>Desktop Effects
i get this messege : 	The Composite extension is not available 
any 1 can help me 
thanks

---

### Post by waggygee on 2007-06-12
What graphics card are you using? Ensure you have the correct video driver if its Nvidia (like mine you'll need XGL) read through this [http://ubuntuforums.org/showthread.php?t=131267](http://ubuntuforums.org/showthread.php?t=131267)

---

### Post by muximus on 2007-06-12
what is your computer's configuration?.. 

the solution would depend on tht

---

### Post by yousufinternet on 2007-06-12
my graphics card is Ati and i have installed the driver from System > Administration > Restricted Drivers manager

---

### Post by wookaru on 2007-06-12
I have the exact same problem.  Radeon 9800 Pro - installed drivers with Envy.

---

### Post by yousufinternet on 2007-06-13
any 1 can help??!!

---

### Post by quinnten83 on 2007-06-13
I can help, vause I don know enough about this subject.
But I have a ATI card too, and it worked pretty much straight forward.
thing is, you use the nvidia drivers and someone else was using envy, aren't this drivers for the wrong card?
add/ remove says that my video card does not need a restricted driver.

---

### Post by wookaru on 2007-06-13
OK, I got mine working.  There werent any magical tricks, i just kept reinstalling ubuntu over and over, trying to enable desktop effects each time.  Eventually one time it worked.

Just out of curriosity, I reinstalled again and desktop effects didnt work anymore.  It took 5 or 6 more installs before I got it to work again...:/  Keep hammering away at it i guess?

---

### Post by Jouke74 on 2007-06-14
Compiz and Beryl require composite extensions. For NVidia you need to download and install the proprietary driver which supports AIXGL and composite. For ATI the proprietary driver does not support composite. As a result you need to install XGL server first (Open gl), which is basically an extra layer between the window managers and the videocard.

Reinstalling Ubuntu 6 times won't change that.... fiddeling around with it afterwards might... reading the Beryl and Compiz websites before doing that, probably saves a lot of time in the end....

---

