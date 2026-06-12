---
title: "NVIDIA FX5200 VGA card driver problem .."
date: 2008-10-20
forum: Desktop Environments
---

### Post by amr_essam on 2008-10-20
Dear there,

i have a problem that's really annoying me
first of all , i have ubuntu 8.04 desktop version and i installed it inside windows.
but when i logged into it , the VGA driver wasn't recognized and the system told me that it has a driver for it :

- before i install this driver , the resolution was 800x600 , and i wasn't able to activate the high visual effects

-after i installed it , the resolution was reduced to 640x480 and the option of 800x600 disappeared but i can activate visual effects

please if anyone can tell me what i have to do , note that it's my first time on ubuntu

Thanks in advance

---

### Post by OuT.Law on 2008-10-20
> **amr_essam said:**
> Dear there,

i have a problem that's really annoying me
first of all , i have ubuntu 8.04 desktop version and i installed it inside windows.
but when i logged into it , the VGA driver wasn't recognized and the system told me that it has a driver for it :

- before i install this driver , the resolution was 800x600 , and i wasn't able to activate the high visual effects

-after i installed it , the resolution was reduced to 640x480 and the option of 800x600 disappeared but i can activate visual effects

please if anyone can tell me what i have to do , note that it's my first time on ubuntu

Thanks in advance


I was just about to start a new topic about this problem cuz i have the same :(

after some research on the internet i found this :

start the terminal and login as a root and type this "displayconfig-gtk" (without quotes) a display wizard should start and from there you can change the display resolution BUT when i change it to 1024.768 @70Hz the monitor turned of (i have a CMD LCD monitor 1280x1024).
after another research i found how to reset the configuration, and i tried to change the monitor from "plug and play" to "LCD 1024x768" and changed my resolution to 1024x768 @60Hz and restart the monitor turned of before the log in windows appear so im now reinstalling UBUNTU.

sorry for the long reply but i hope you can change your resolution and i hope someone will help me with my problem !!! :(

---

### Post by amr_essam on 2008-10-20
> **OuT.Law said:**
> I was just about to start a new topic about this problem cuz i have the same :(

after some research on the internet i found this :

start the terminal and login as a root and type this "displayconfig-gtk" (without quotes) a display wizard should start and from there you can change the display resolution BUT when i change it to 1024.768 @70Hz the monitor turned of (i have a CMD LCD monitor 1280x1024).
after another research i found how to reset the configuration, and i tried to change the monitor from "plug and play" to "LCD 1024x768" and changed my resolution to 1024x768 @60Hz and restart the monitor turned of before the log in windows appear so im now reinstalling UBUNTU.

sorry for the long reply but i hope you can change your resolution and i hope someone will help me with my problem !!! :(



Dear ,
i just want to know how to login as a root ??
because when i type "displayconfig-gtk" it tells me that i have to be administrator
hope we solve this problem soon because i spent all the day trying :|



Regards ,

---

### Post by eragon100 on 2008-10-20
> **amr_essam said:**
> Dear ,
i just want to know how to login as a root ??
because when i type "displayconfig-gtk" it tells me that i have to be administrator
hope we solve this problem soon because i spent all the day trying :|



Regards ,

type sudo displayconfig-gtk

sudo means: run the next command as root.

---

### Post by OuT.Law on 2008-10-21
amr what happened with you ? did it worked ?

and you guys can't you help me with my problem ? this is ubuntu forum if you cant help, than who can ? :(

---

### Post by amr_essam on 2008-10-21
> **OuT.Law said:**
> amr what happened with you ? did it worked ?

and you guys can't you help me with my problem ? this is ubuntu forum if you cant help, than who can ? :(


Dear outlaw,

actually it worked thanks god , i was about to get back to windows again :) but anyway i will tell u what i did:

- i re-installed the ubuntu again on my system , then i let it install the driver that he wanted for the VGA.
- i restarted my computer , then i wrote the command "sudo displayconfig-gtk"
and then i chose my type of screen and increased the resolution then restarted the PC , so it worked
try that and i hope that it works


Regards and really thanks for the help
Amr

---

### Post by OuT.Law on 2008-10-21
> **amr_essam said:**
> Dear outlaw,

actually it worked thanks god , i was about to get back to windows again :) but anyway i will tell u what i did:

- i re-installed the ubuntu again on my system , then i let it install the driver that he wanted for the VGA.
- i restarted my computer , then i wrote the command "sudo displayconfig-gtk"
and then i chose my type of screen and increased the resolution then restarted the PC , so it worked
try that and i hope that it works


Regards and really thanks for the help
Amr


dunnu i just tried this before but it did't work for me, i can find my LCD in that list :|
i downloaded the driver from nvidia and now i have some new problems because i have to exit xserver to install the driver, exiting the x server mean i have to do like this :
in terminal write sudo -s
after that "telinit s" 
than i should install the driver without any problems BUT doing so make my Keyboard go crazy and i cant do anything only restarting the computer.

so guys any solution ?!? :confused::(

---

