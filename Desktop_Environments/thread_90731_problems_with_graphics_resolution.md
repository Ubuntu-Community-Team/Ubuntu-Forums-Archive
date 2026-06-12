---
title: "problems with graphics resolution"
date: 2005-11-15
forum: Desktop Environments
---

### Post by pyro on 2005-11-15
hello!
i'm kinda new to linux world, but better now then never.

so - i downloaded ubuntu 5.10 dvd, and installed it on the virtual machine (just for testing).
everithing seems fine, but when graphics mode starts up it gets all mixed up, and virtual machine says something about trying to display resulution not aviable to my monitor.

when setup wizzard asked for resolutions i checked 1280x800, 1024x768, 800x600 and 640x480 (all aviable to my monitor)

i have fujitsu siemens amilo a 1630 (ati mobility radeon 9700 128bit, 128mb graphics) with ws monitor.

microsoft virtual pc 2004

any help?

---

### Post by bryan986 on 2005-11-15
Try only selecting 800x600, I think the limit of the virtual machine is something less than what your monitor actually supports

Also if you have the option, choose something less than 24bit color

---

### Post by arthursdomain on 2005-11-16
im having the same problem and also basically doing the same thing, running a virtual machine 2004, it seems like the screen is too large then it starts to distort the image, im able to login and what not, but i guess its a resolution problem.  What i did was uncheck all the displays except the lowest which is like 640x400 or something, but that didnt work either.  Im going to try the 800x600 one now.  It might be something else though, anyone know know of known conflicts with either Virtual Machines and Ubuntu or does ubuntu only allow certain graphic cards?

---

### Post by arthursdomain on 2005-11-16
The directions I found on this website didn't work (no emacs + config file name is different). The following directions actually worked for me using Hoary 5.04 from recovery mode: 

If your a real noob like myself, then couple things you need to know to start this in recovery mode you must press ESC when its booting up, it will ask you like about 30 secs from when you start the vmachine, secondly pick (recovery) let the thing boot up normally, it will give u a lot of text, once you get a prompt should be root@something> type cd.. kind like dos, then start on step 2 -- also note: everything is case sensitive so you need to type capital X and 1 1. the rest is prety simple, and once you reboot, it will work.

1. Log into another virtual session as root 
2. # cd /etc/X11 
3. # pico xorg.conf (to edit xorg.conf) 
4. Now, scroll down in pico to Section "Screen" and find the entry 
named "DefaultDepth". Change the setting you find there from 24 to 16. 
5. Ctrl O 
6. Enter 
7. Ctrl X 
8. # reboot

---

### Post by scarem on 2005-11-26
Hi 

Another newbie here, also getting his feet wet with Ubuntu/MS Virtual PC &#8211; same problem as above (color depth distorting graphics), but with 5.10 this time

Being a newbie I need to follow step by step instructions, but when I follow the instructions to resolve this in the ['how to']("https://wiki.ubuntu.com//HowToConfigureUbuntuForMicrosoftVirtualPC2004") , I appear to get a blank xorg.conf; is this more likely to be an installation error (2 installs with same problem?), or would the procedure to rectify the color depth have changed with the 5.10 release?

Thanks

---

### Post by scarem on 2005-11-26
Ignore my question above - I ditched MS Virtual PC in favour of VMware.

---

### Post by KermitJr on 2005-12-01
I was having trouble with several older video cards and a particular monitor and kept getting 640x480 no matter what I did for modes, etc.  

HOWEVER, when I went back one time and ran
```
sudo dpkg-reconfigure xserver-xorg
```

I entered the actually amount of RAM on the video card (one was 4096 and another 2048) and PRESTO! My Modes line worked as normal with or without monitor on boot.

So try entering in the actual video RAM you have and that should hopefully fix your error.

If not, troubleshoot by looking for the actual error messages in the /var/log/X11/xorg[tab].log file.

Hope this helps!
KermitJr

---

