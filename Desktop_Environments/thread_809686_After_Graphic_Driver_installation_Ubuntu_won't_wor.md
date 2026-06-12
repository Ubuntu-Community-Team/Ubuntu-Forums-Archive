---
title: "After Graphic Driver installation Ubuntu won't work!"
date: 2008-05-27
forum: Desktop Environments
---

### Post by primky on 2008-05-27
This is the problem:
I go to System->Administration->Hardware Drivers. There i select ATI accelerated graphics driver (I have Radeon x1650). When i reboot, Graphic interface doesn't start. The last thing i see is Ubuntu logo and loading bar bellow.

What to do? Any alternative?

---

### Post by cybernet on 2008-08-04
no answer
come on i have the same problem :confused:

---

### Post by geezon on 2008-08-06
Same problem for me :(
i reinstalled (i hadn't done much on there anyway) and haven't installed the driver this time. but i would like them installed and working.

---

### Post by overdrank on 2008-08-06
Have you all tried Envy. :)

---

### Post by Vorian Grey on 2008-08-06
The blank screen probably means your video cards aren't compatible with the newest driver, which is what you get when you use the Hardware Drivers. Don't feel bad, my card doesn't work with it either. I used EnvyNG and it pulled in the driver I needed and installed it and set everything up.

---

### Post by ahickey on 2008-08-06
I had the same with an NVIDIA card.
Ubuntu started but the resolution/refresh rate was not supported by my cheap LCD monitor

If you have speakers - can you hear the Ubuntu sound of the login screen.
If so login. I know you cannot see anything, but just login.
Then you should hear the full Ubuntu welcome sound.

Now press [ctrl]+[alt]+[numeric keypad +]
This will change the resolution so see if a lower resolution works.
Once you have a desktop then right click on Application and select edit.

Under Other there is somethig like [display].  Add this to the menu.
(Not on Ubuntu at the moment, so can't remember it off the top of my head)
Obvioulsy, select this application.
Here you can change your monitor.
If your actual monitor is listed select it otherwise select one of the defualt monitors with the same resolution as yours.
Test it and see if it works.

For me I had to select a CRT monitor and not the LCD (even though I have an LCD monitor) as the login screen still didn't appear.

I hope this helps.

---

