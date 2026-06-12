---
title: "Dual monitors"
date: 2008-02-15
forum: Desktop Effects &amp; Customization
---

### Post by awilisch on 2008-02-15
I recently installed Gutsy on my workstation, have two Dell widescreens. I managed to get all the desktop effects working, and things seem to be working fine except that everytime I start something, it centers it directly BETWEEN the two monitors. It's quite annoying. I'm running the restricted nvidia drivers and I THINK I'm running in Twinview with the xgl xserver. 

Does anyone know how I can make things appear on the main monitor instead of directly between them?

Thanks much
--Aric

---

### Post by mrmiserable on 2008-02-15
could be a setting in compiz 


ccsm/desktop cube/mutil output mode

---

### Post by PinkFloyd102489 on 2008-02-15
Mine used to do that also, I dont have dual anymore. I never found out a fix for it either. :-/

---

### Post by White_Panther on 2008-02-15
if you have an nvidia card i found that this command will help a lot to setup your dual monitor

```
gksudo nvidia-settings
```

---

### Post by awilisch on 2008-02-19
Nvidia-settings worked fine until I installed the xserver-gl package. Now when I go into it I get an error saying I'm not using the nvidia drivers. I know that I am from the big NVIDIA splash screens that come up before the xserver starts, but nvidia-settings doesn't seem to recognize that. I'm wondering if it's looking in the /etc/X11/xorg.conf file instead of wherever the config file is for xserver-gl. 

The graphics all work great. The only thing I can't get to work is the opening of windows between both monitors, and that I can't seem to get the desktop cube to appear even though it's configured....but that's another issue. 

If anyone can think of anything I'm open to any help. :)

--Aric

---

### Post by FuturePilot on 2008-02-19
Remove XGL. Nvidia cards do not need XGL. It just causes problems like the nvidia-settings problem

---

