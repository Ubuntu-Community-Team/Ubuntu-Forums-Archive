---
title: "ubuntu doesnt get past splash screen"
date: 2009-03-08
forum: General Help
---

### Post by yehgross on 2009-03-08
i had resolution problems and i realised i might have had the wrong driver, so i installed nvidia linux driver 180.29. i hit ctrl alt f1, stopped X and installed it and it all went great but when i restarted the computer, it doest get past the load screen, it just goes black. i can press ctrl alt f1 and can type in commands but i cant go into a graphics mode. i hope that made sense. how can i solve this?? im running the live CD right now.

---

### Post by yehgross on 2009-03-08
anyone? should i just reinstall ubuntu?

---

### Post by rmausser on 2009-03-08
this happened to me. When booting up GRUB hit Escape and go into the menu for different boot ups. 

Select your latest Kernel's (the one closest to the top) Recovery Mode. 

Once it loads, select "fix xorg" (or "fix xserver" or whatever its called) 

It will bring xorg conf back to defaults. 

Now after it completes boot normally. 

You must remove the driver now.

Go to

 [http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+180+black+screen](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+180+black+screen)

for removal instructions. 

Reboot computer again. Reload 177 drivers. 

I don't know the correct way to load 180 drivers. But this  will fix your system

Rob

---

### Post by yehgross on 2009-03-09
ive tried that and it wouldn't work, so i just installed it again over it. i never had anything on there anyways. BUT, i installed the 173 drivers (even thought they wouldnt work before, i think) and forgot about it. Turned my computer on today and tada, finally worked. Maybe i didn't try the 173 drivers, haha. thanks for the help

---

