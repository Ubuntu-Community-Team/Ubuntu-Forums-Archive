---
title: "Screen Resolution Issue"
date: 2007-11-13
forum: Desktop Environments
---

### Post by Zipster90 on 2007-11-13
I've been having issues with my video resolition ever since I tried to hook up my computer to a projector to no avail. I plugged it into the projector, pushed Fn+CRT/LCD (On a Dell E1505,) and nothing happened. I tried multiple times before giving up.

After I disconnected the VGA cable, every time I reboot my laptop it boots into 640X480 resolution, with no option to change it. I end up having to go to Screens and Graphics and switch to a higher resolution LCD panel in order to get it back to normal. It used to work perfectly on its own with the plug and play and now I must do it every time I reboot. Anyone have any ideas? Should I reinstall Gnome, Ubuntu altogether, or is there and easier way? Thanks! :)

---

### Post by circuitsurfer on 2007-11-21
Hello I have the same problem every time I reboot or logoff it reverts to 1280x768 but and I keep going and resetting it to 1280x1024. What up with this strange behaviour, Everything else works fine

I am using an ATI Radeon pro 9200.  Ubuntu 7.10 with the latest patches.

PS tip of the day, WEBMIN is the best tool for configuring your ubuntu drives and networks.

Serge

---

### Post by Toadmund on 2007-11-21
Me too, xpress 200g series, I have to change the xorg back to what worked (it keeps changing itself) :mad: , then I have to reset my resolution back to 1024 X 768 and my video driver back to 'radeon' from 'vesa'.
And sometimes I got to re-check the enable driver button in RDM.

When I reboot it resets itself to 1280 X 1024 or worse, disable the driver (8.42) altogether.

I need some advice too please, I just want to turn on my comp and use it.

PS, I can't use compiz either because xgl screws things up. So xgl is un-installed for me, I really like compiz too, damn shame.

---

### Post by skyjacker on 2007-11-21
SAme here. Whenever I restart my PC (I dual boot with XP for a while longer), I have to reset the resolutions to what it was before the restart.:confused:

---

### Post by mrmiserable on 2007-11-21
i had this issue also with ati card X600 the way i kept my resolution was to goto 

system/preferences/screen resolution and set it at eg 1280x1024 and tick box make default

i think the ati driver resets every reboot and gives this problem

give it a go it might work for you

---

### Post by unxzst on 2007-11-21
im having the same story with geforce2 go, works ok with external svga to my tv, but no selection in Screen Resolution Preferences. I can't even look at /var/crash/_usr_bin_displayconfig-gtk.0.crash because i dont have permission. crazy!@?
i installed the proprietary video driver, maybe thats why...

this thread: [http://ubuntuforums.org/showthread.php?t=279407](http://ubuntuforums.org/showthread.php?t=279407)
and fiddling with Restricted Drivers helped. in the end... i lost a little time, and ubuntu sucks a little more.

---

