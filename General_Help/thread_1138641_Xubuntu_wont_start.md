---
title: "Xubuntu wont start"
date: 2009-04-26
forum: General Help
---

### Post by Luiggipro on 2009-04-26
Hi, I just installed xubuntu jaunty in my old celeron pc, everything was fine yesterday, I installed the nvidia drivers for my Fx5200, I installed all the software I wanted, I also rebooted and after that it booted fine. But today xubuntu dont start :confused:, It stops with a light blue screen with the mouse cursor able to move, but then I wait like 20 minutes and nothing happens. I had to ctrl+alt+f1 and do the next things to get to the login screen: sudo killall gmd and sudo gdm stop and then I started in a xterm failsafe and Im able to acces firefox and thunar. Any help would be very appreciated. :guitar:
PD: im using ext4, I also have ext4 in ubuntu jaunty in my other pc (amd phenom, 4gb ram, ati radeon hd 4670) and it is working unbelievable fast and stable

---

### Post by rotary12 on 2009-04-26
same thing here

---

### Post by Luiggipro on 2009-04-27
well, Its solved now. I had to format my hard drive ... just kidding :lolflag: When the cursor appears press alt+f2 and run xfce4-panel to recover the panel and xfdesktop to recover the desktop. If xfdesktop doesnt work, go to the menu, settings, desktop settings and activate "allow xfce to manage the desktop". Then go to "Settings -> Sessions and Startup" and choose "automatically save sessions on logout"
:guitar:

---

### Post by jvijayv on 2009-05-05
Well... I have the same problem. I upgraded all the way from Gutsy to Jaunty using the update manager. (was a bit painful but I did it anyways)

During the Last upgrade from Ibex to Jaunty, my laptop battery drained out and in the middle of 'installing packages'. I restarted the machine and it came to a black screen. I completed the upgraded using the command line. But, when I reboot the laptop, it loads fine to the blue screen with the circular 'please-wait' cursor. But then, the cursor never changes to an arrow icon. I did what the first person in this post did. i.e. go to a command prompt, kill gdm and stop gdm.

Startx sometimes works for me partially. The wallpaper shows up correctly and that's about it... 

If you guys find out anything about this issue, please post the details here. Any help is appreciated.

Thanks,
-Vijay

---

