---
title: "Installation woes"
date: 2006-07-17
forum: Desktop Environments
---

### Post by jgc on 2006-07-17
Morning,

Slightly baffled ](*,) 

I have attempted to install ubuntu (ECS K7VTA mobo / Athlon XP 2400, 512 RAM, 80Gb IBM Deathstar), but it won't have it ... well sometimes :-?  ... I have tried the desktop and alternate installs ... sometimes (after install) it works on login, run the updates, reboot, login and it just goes to a blank (dark brown) screen with pointer?


Other times it won't even do that after install ... login screen and just straight to the blank (dark brown) screen with pointer?

I have tried different CD's, HDD's, Memory, CD Rom ... but still the same ... any ideas?

---

### Post by Sef on 2006-07-17
What are your system specs? (Include the video card for likely the problem lies with that.)

---

### Post by jgc on 2006-07-17
My spec is as follows;

ECS K7VTA mobo
Athlon XP 2400
512Mb RAM
80Gb IBM Deathstar

I have tried various gfx cards ... I am currently running an Nvidia 6800 Ultra (256) (Geforce6 series)

All of the cards, both old and new have been Nvidia chips ... same thing happens ... nice login screen then nothing ... just a dark brown screen and pointer? :confused:

---

### Post by thoolihan on 2006-07-17
Go to a terminal (Ctrl-Alt-F1) and try to copy /var/log/Xorg.0.log
to another computer or floppy and post it here...
-Tim

---

### Post by jgc on 2006-07-17
Well I have made progress! :mrgreen: 

First of all I installed the Nvidia drivers;
```

sudo apt-get install nvidia-glx nvidia-kernel-common 
sudo nvidia-glx-config enable

```
Then went back to the login screen ... still no joy, the screen remained brown, flicked back to the login and the screen just fragmented ... so I rebooted and manually upgraded;
```

sudo apt-get update
sudo apt-get upgrade

```
I attempted to restart;
```

sudo /etc/init.d/gdm restart

```

... which failed, so I rebooted the box and bingo! :mrgreen: 

Thanks for your help, and for sending me down the right path! :cool:

---

