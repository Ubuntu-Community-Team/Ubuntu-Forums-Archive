---
title: "Gutsy - Problems with screen and graphics / X"
date: 2007-10-23
forum: Desktop Environments
---

### Post by tjotjos on 2007-10-23
Hello. I just upgraded from Feisty to Gutsy today after having used it since it came out. Everything was going smoothly until I tried to use "Screens and Graphics" to create a dual monitor setup. After picking the settings I wanted, I clicked OK and it proceeded to restart X. At this point the screen just turned black and stayed that way for awhile. I ended up having to manually power off the computer. When I restarted, I did have dual monitors, however, not in the order I arranged or with the correct resolutions. This black screen issue also occurs if I try using ctrl+alt+backspace to restart X or ctrl+alt+F2 to drop to the console. I had none of these problems under feisty, and the dual monitor set up was working when I manually set X myself to do it. Any help resolving this issue would be greatly appreciated!

System Specs:
Toshiba Laptop (P15-S470)
Intel P4 3.0 GHz
512 M Ram
Nvidia G-Force FX Go5200 64M

Let me know if any other info is needed!

Thanks! -TK

---

### Post by ahm911 on 2007-12-06
Hey man i have a similar problem... i was using xorg with no prevail.. until i found out abt graphics and screens. I set up my external monitor ( the plasma screen i have used for catia drawings n such ) but when i restarted i get a blank screen its i get sound when i log on ( when i blindly type in my name n password ) but no avail i tried restarting .. i would like to retrieve my original settings without formatting or reinstalling.

any ideas?

---

### Post by Happy_Man on 2007-12-06
If you have it, why not use nvidia-settings to set it up? ```
sudo nvidia-settings
```

---

