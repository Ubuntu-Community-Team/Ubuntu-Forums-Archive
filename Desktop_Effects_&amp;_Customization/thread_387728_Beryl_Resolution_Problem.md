---
title: "Beryl Resolution Problem?"
date: 2007-03-18
forum: Desktop Effects &amp; Customization
---

### Post by UKDragon on 2007-03-18
Im a newb to ubuntu, so I used the Beryl installation script to get the fancy bells and whistles, or so I thought.  (Instructions I used were here: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI))

Whenever I try to boot into it now, I get an error message from my Monitor to say it cannot support the display mode, and optimum resolution is 1280x1024 60Hz.

So is there any way I can disable it without booting into ubuntu, or changing the resolution or whatever, as otherwise looks like a reinstall :( 

Its a Dell 1907FP LCD Monitor on DVI from Radeon X800 GTO.

---

### Post by Kobalt on 2007-03-18
Yes there is a way. When you get to the point of you receive that error message, pres Ctrl+Alt+F1 to access a command line. Log in with your username and password then enter the following command line : 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
From there, select the maximum resolution you want your monitor to operate at with the spacebar, then press Enter. 
Finally, reboot your computer, and it should do it. 

If you still get error messages, then you might need to reconfigure your whole X server then...

---

