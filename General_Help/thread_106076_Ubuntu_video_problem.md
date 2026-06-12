---
title: "Ubuntu video problem"
date: 2005-12-19
forum: General Help
---

### Post by Masteroc on 2005-12-19
Hi,

I have a new installation of ubuntu 5.10. When i started it up and logged in, everything was fine until about 3-4 minutes after i had logged in and was using it. Then the screen went crazy and there were just striped lines (the the ones on tv when a channel is testing) excpet they wre only white. I restarted and tried again. Same thing happens. It is not any particular progam becuase a different one was running each time.

Thanks for helping!

---

### Post by 23meg on 2005-12-19
Noone can help without knowing anything about your configuration. What's your video hardware? Which driver are you using?

---

### Post by Masteroc on 2005-12-19
I have a very old video card. I think that it is a Trident 3D image 9750.

I dont know what driver i am using. just the one that ubuntu installed when i installed. 

I can most likely get the driver if it would help.

How would i install it?

---

### Post by 23meg on 2005-12-19
Please post the "Device" section of your /etc/X11/xorg.conf file.

---

### Post by dickohead on 2005-12-19
Before changing anything physical or playing with drivers, just drop your screen resolution back to something safe ie: 800x600 / 640x480.

Edit the following file like this:

sudo vi /etc/X11/xorg.conf

Then find the lines where it lists the display depth (8,16,32 etc) and remove the entires that are higher than 800x600 or 640x480, and then restart the x-server (Ctrl+Alt+Backspace).

---

### Post by brenick on 2005-12-20
I have a similar problem. 

If I log out and then log back in, the screen returns to normal.

The device section of /etc/X11/xorg.conf is
Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Driver          "nv"
        BusID           "PCI:2:0:0"
EndSection

---

### Post by invalid on 2005-12-20
Consider then, using the nvidia drivers, rather than the generic nv version.

---

### Post by Masteroc on 2005-12-20
hey dickohead,

thanks alot, that worked. I reduced the screen resolution and it was fine.

thanks!!

Now if only i could get my ethernet working...([http://www.ubuntuforums.org/showthread.php?t=106079](http://www.ubuntuforums.org/showthread.php?t=106079))

---

