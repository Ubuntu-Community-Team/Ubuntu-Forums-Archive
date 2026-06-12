---
title: "how to install vesa"
date: 2008-12-19
forum: General Help
---

### Post by jamesclayden on 2008-12-19
i have been doing some research and in looks like in need to install the vesa drivers on my system. i am on ubuntu 8.04 an have a radon x1950. 

Is there a how to on installing these drivers?

can i have a bit of help on this, cheers.

---

### Post by plucky on 2008-12-19
> **jamesclayden said:**
> i have been doing some research and in looks like in need to install the vesa drivers on my system. i am on ubuntu 8.04 an have a radon x1950. 

Is there a how to on installing these drivers?

can i have a bit of help on this, cheers.

If you haven't installed  any hardware drivers,then you might already be using the vesa driver.Please post the output from a terminal window of ```
cat /etc/X11/xorg.conf
```

First try **System > Administration > Hardware Drivers** and see if your system can find the appropriate driver for your video card.

To change the driver you can use ```
gksudo displayconfig-gtk
```


Good Luck

---

### Post by jamesclayden on 2008-12-19
i managed to install vesa and it is the only driver that works with the radon X1950 card. for other peoples referance all i did was make sure that the closed source fglrx driver was not enabled or installed then added

```
	Driver		"vesa"
``` 

to the Device section of the xorg.conf file. Advice on how to mod that is available from people more experienced than me but be careful cos it can prevent your system from loading if not done correctly.

---

