---
title: "Nvidia card and Compiz Fusion"
date: 2007-08-07
forum: Dell  Ubuntu Support
---

### Post by circuz_phreak on 2007-08-07
My system specs are as follows: Dell Inspiron 1720 notebook, dual core 2ghz processor, 250 5400rpm sata drive, 256 Nvidia GeForce 8600GT graphics card....

I want to get compiz fusion going but here´s my predicament.  In order to get ubuntu up and running I needed to use the alternate cd, then in order to get x started i had to edit the /etx/X11/xorg.conf file and change default driver from ¨nv¨ to ¨vesa¨.  I went to synaptics package manager and downloaded the nvidia-glx package (binary drivers)....the xorg.conf file still has vesa as the default driver....is this a problem?  I don´t really understand the diffrence in using vesa or nv...newb here...Even if i wanted to get the latest drivers from nvidia site I can´t exit x and go to a command line...when i type sudo /etc/init.d/gdm stop it exits x server but after it does i don´t get a command line terminal, i am just able to type anything without a response, have to reboot...is this a problem or are my concerns pointless?  Any help would be awesome.

---

### Post by dreadlord_chris on 2007-08-08
instead of just opening a terminal and stopping X you'd be better off doing it this way:
Control-Alt-F1
This will bring you to a virtual terminal (vtty1) that you can log in to - do so...
Now stop X
```

sudo /etc/init.d/gdm stop

```
from here you can install the binary drivers from NVIDIA
To use the new drivers you need to change, in xorg.conf, **vesa** to **nvidia**
There are some other things you can add to get fuller capabilities from the card - we'll get to that after we get you up & running though...
Once you are done installing & enabling the driver in xorg.conf:
```

sudo /etc/init.d/gdm start

```

---

### Post by circuz_phreak on 2007-08-08
Thanks, followed your suggestion.  I have the nvidia-glx binary drivers installed, but when switching /etc/X11/xorg.conf from ¨vesa¨ to ¨nv¨ or ¨nvidia¨ x fails to load....screen flickering and the cryptic error message come back (just like before).  What if I download the latest driver from the nvidia website, that driver even trys to reconfigure the xorg.conf file itself....i&#314;l give it a try.  But this is strange...if my card too new for ubuntu or what?

---

### Post by Obor on 2007-08-08
This is how I got my nvidia 8600GT working few days ago:
[http://www.robdian.co.uk/content/view/56/](http://www.robdian.co.uk/content/view/56/)

---

### Post by dreadlord_chris on 2007-08-08
> **circuz_phreak said:**
> Thanks, followed your suggestion.  I have the nvidia-glx binary drivers installed, but when switching /etc/X11/xorg.conf from ¨vesa¨ to ¨nv¨ or ¨nvidia¨ x fails to load....screen flickering and the cryptic error message come back (just like before).  What if I download the latest driver from the nvidia website, that driver even trys to reconfigure the xorg.conf file itself....i&#314;l give it a try.  But this is strange...if my card too new for ubuntu or what?

I do believe this is the driver you need for your card:
[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)

The nvidia-glx package is definately wrong for your card - you need to uninstall it

You can follow the steps provided in the link by Obor, they should work fine...

---

### Post by aldenhg on 2007-08-08
It would probably be easier for you if you used a program called Envy to install your driver.
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu6_all.deb)
Run the .deb and then go to the System Menu -> System Tools -> Envy. It's pretty straightforward from there. 
Just a note - when I used Envy it made the default depth 16 instead of 24. If you want to run Compiz Fusion you'll need to change the default depth in the screen section of your xorg.conf file to 24.

---

### Post by circuz_phreak on 2007-08-09
Thanks guys, gonna try using the page obor provided, i heard envy wasn´t the best route to go down.  I remember hearing about the default depth situation, also many others.  I´m gonna search the forum for threads that follow similar system specs as mine regarding compiz fusion....too busy to give this a go untill the weekend, so i guess i´ll post again if i get stuck sometime this weekend.  Thanks guys.

---

### Post by zeddock on 2007-09-14
> **circuz_phreak said:**
> Thanks guys, gonna try using the page obor provided, i heard envy wasn´t the best route to go down.  I remember hearing about the default depth situation, also many others.  I´m gonna search the forum for threads that follow similar system specs as mine regarding compiz fusion....too busy to give this a go untill the weekend, so i guess i´ll post again if i get stuck sometime this weekend.  Thanks guys.

How did it go?
zeddock

---

