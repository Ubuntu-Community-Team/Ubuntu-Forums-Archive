---
title: "Dell inspiron N4110 low battery life"
date: 2011-11-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Xanza on 2011-11-21
I'm running 11.10 on a Dell Inspiron n4110 and i notice a full battery charge only gets me 2 hours and 35 mins of battery as opposed to my windows 7 which is getting 4-5 hours. I'm new to Ubuntu , is there any power saver mode or any tweaks to make the battery life longer?

PS: I also learned that by turning off bluetooth my wireless gets turned off  too, is there a way to just turn off bluetooth?

---

### Post by majedaly on 2011-11-21
Why not to try the screen brightness? The screen consumes a lot of power on it's own.
Also, check your bios for power saving features (would be called something like speed step) which basically reduces the processor power  when on battery

---

### Post by Xanza on 2011-11-21
> **majedaly said:**
> Why not to try the screen brightness? The screen consumes a lot of power on it's own.
Also, check your bios for power saving features (would be called something like speed step) which basically reduces the processor power  when on battery

Thank you for the quick reply. My brightness is already set to 40% , forgot to mention that. I'll try the bios power saving features

EDIT : Speedstep is enabled by default.

---

### Post by Xanza on 2011-11-23
Still nothing after more than one day of finding a solution. after fully discharging and recharging i get around 2 hours and 50 minutes. Still no comparison to my windows 7. I have no other ideas.

---

### Post by bayonaaar on 2011-12-26
I have the same notebook.
Try Ubuntu Natty Narval 11.04 with with core 2.6.38 or 2.6.39. Ubuntu 11.10 and a core 3.0+ has a problems with powersaving. After installing 11.04 use uppdate manager to update system but don't apgraid it to 11.10. Install a powertop and run it in terminal :
sudo powertop. 
This program will help you to optimise your system. But it will optimise only when is running. You can automate powersaving by using some scripts (look in google).

Tel me please is it working youre intell   *WiMAX* 6150 device? I cant make it work.

---

