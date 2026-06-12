---
title: "D610 and docking station on Gutsy - system freezing with external video"
date: 2007-10-19
forum: Dell  Ubuntu Support
---

### Post by sarcangeli on 2007-10-19
Hi all,
I have a Dell Latitude D610 with a docking station. 
With Ubuntu 7.04 and the ATI driver everything was working nicely, except that i had to manually adjust resolution of the external screen to 1280x1024 each time (I know there was a way to get this automatic but i never spent time on it).
I upgraded to Ubuntu 7.10, disabled the ATI restricted driver (i saw that the free one is not that sluggish anymore) and enabled the compiz effects.
Everything works fine when i'm using just the laptop.

If i connect it to the docking station it recognizes the new monitor and adjusts the resolution automatically (wow!), but the bottom task bar is not displayed, and the system freezes on the first task that i try to ask.

Did anyone experience (and solve) something similar?

thanks,
silvio

---

### Post by bluedragon436 on 2007-10-21
I have not even attempted to try docking my D610 since I installed 7.10.  I will try it out tonight and try and get back on here tomorrow and let you know what I find out.

---

### Post by sarcangeli on 2007-10-22
Correction to what i wrote. When i plug the docking station and boot Ubuntu it automatically recognizes the external monitor, but doesn't change the resolution (still 1400x1050, while the external monitor supports at most 1280x1024).
I can manually adjust the resolution to 1280x1024, but still the system is then going to freeze very soon.

---

### Post by mh1272 on 2007-10-30
I also have a Dell D610 with Dell's basic dock (no hd or CD/DVD).  The monitor is an Acer 20" widescreen LCD.  I am running Ubuntu on a 60GB, 7200ROM HD with 1GB of RAM.

The only issue that I have experienced is putting the D610 into the dock while the laptop is runing does not activate the Acer LCD.  The mouse, keyboard, and USB ports work properly.  A reboot fixes this.  (I haven't tried a logout/login which may do the same thing.)

I am able to change screen resolutions while in the dock without problems.  The Acer will do 1280x800 and fill the whole screen; 1400x1050 leaves "black boxes" on either side.  That is, at 1400x1050, the output reverts to a non-widescreen display.  I have set the resolution to 1280x800 as the default and 1400x1050 has the default.  Everything has functioned as expected.

With the Ubuntu, native drivers, the screen defaults to 1400x1050.  With the restricted, ATI drivers, the lower resolutions are options.  I prefer the 1400x1050 so the restricted drivers are not needed in my situation.  I have not experienced any freezing, hiccups, etc.

7.10 and 7.04 work the same in my setup.

---

