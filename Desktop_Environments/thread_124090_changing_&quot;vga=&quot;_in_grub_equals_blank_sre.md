---
title: "changing &quot;vga=&quot; in grub equals blank sreen on shutdown/reboot"
date: 2006-01-31
forum: Desktop Environments
---

### Post by ajkeys on 2006-01-31
I changed the "vga=" to "vga=0x31A" (which is 1280x1024 at 16bit color) in grub and when I do that, it causes there to be a blank screen on a reboot or shutdown instead of displaying the usual stuff of unmounting drives etc. The computer continues to shutdown and it does NOT lockup, I just can not see what it is doing. It is quite irritating.  When I boot up it works fine only on the shutdown. I did some research and I think it may be caused by usplash running at shutdown, but I could be wrong. If so how do I disable usplash, without uninstalling it. I really do not know what causes the blank screen. help.

---

### Post by awi on 2006-01-31
Have you tried with [COLOR="YellowGreen"]vga=ask[/COLOR] to see if your video card supports that mode? 
Besides, not all the modes works on all the video cards, console resolution (VESA) is not the same as your X Server resolution.

---

### Post by ajkeys on 2006-02-01
I understand that the console and x server resolutions are two different things. That is why I decided to change the resolution on the console so that I get clearer text, more room, etc... I have no complaints with the x server resolution and no complaints with the console resolution I selected. On boot up the console works GREAT. The resolution is 1280x1024(verified by the monitor) and I can see all text clearly. There are no problems. 

Well, after doing more troubleshooting I found that if I disable the automatic startup of gdm or X. I can stay in the console as long as I want and go to each different terminal(Ctrl,Alt F1-F6) and it works fine. Also if I issue a reboot or shutdown the machine will shutdown fine and I can see everything.

Now, when I execute "startx" or allow gdm to start at boot, as soon as I try to shutdown or exit Xserver, it will either show a blank screen or a garbled screen that I can not read.
OR
When the Xserver is running and working and I try to Ctrl,Alt F1-F6 to go to a different terminal every terminal is unreadable.

Note: When I leave the "vga=" at the default setting everything appears to work fine. 

**_RECAP_**: Short and simple, whenever I try to exit Xserver or go to a different terminal with Xserver running my screen goes blank or gets garbled.

Sorry for the length, but I am trying to be as detailed as possible to hopefully get straight to the point.

System Specs:
DFI Lanparty Ultra-D
Geforce 6600GT PCIEX
1gig mem

**edit:**
I also wanted to add that I do not use the splash thing and have removed it from my menu.lst file in grub.

---

### Post by ashrack on 2006-02-01
I am also very intersted in this. 
So could some help>

---

### Post by steve.horsley on 2006-02-01
I'm not sure if it takes hex numbers. Try vga=792.

---

### Post by ajkeys on 2006-02-02
I figured it out. :-D  All I did was unplug the TV that was hooked up to my video card. 

I think the problem is that the TV can only do 1024x768 and the monitor is trying to do 1280x1024 so it freaks out and does not work.

So in theory,
If you had two monitors that had two different max resolutions (say 1280x1024 on one monitor and on the other say 1024x768 or any combination of resolutions) You should run into the same problem or is it strictly a TV issue. Can anyone confirm this? or Does anyone have a solution? :-k

**edit:**
I did a little testing and If you set the resolution to a resolution that both monitors (or TV) can do then everything works fine. That actually makes a lot of sense, but I still wish I could keep my TV connected and use the higher console resolution.

Also,
[QUOTE=steve.horsley]I'm not sure if it takes hex numbers. Try vga=792.[/QUOTE]
It does not seem to make any difference whether you use hex or integer values

---

### Post by ashrack on 2006-02-02
STEVE.HORSELY
HEX numbers or normal numbers are irrelevant. Since GRUB automaticly interprets them. 
AJKEYS
4M it is  not related to having a TV plugged in, since I use only 1 monitor and still can't set VGA=0x318 which interprets as 1024x768x24 and VGA=0x317 = 1024x768x16. But I get garbled terminals or blank screen, thou X works fine. 
Will try starting the machine without GDM and see what happens.(haven't rebooted this baby in 2weeks)
Will keep U posted.

ps. I2 am not using USPLASH, I have it purged from GRUB and SYS-V-INIT scripts. I hate splash screens.

---

### Post by ajkeys on 2006-02-02
Just to see what happens you should try 16 bit color just to see if it works, but when I get back I will also try the 24 bit color.

Also, Do you get a blank screen on bootup? The only time I ever got a blank screen or garbled terminals was after X had been run. Before X ran my terminals worked fine even with the TV plugged in.

---

### Post by ashrack on 2006-02-02
[QUOTE=ajkeys]Just to see what happens you should try 16 bit color just to see if it works, but when I get back I will also try the 24 bit color.

Also, Do you get a blank screen on bootup? The only time I ever got a blank screen or garbled terminals was after X had been run. Before X ran my terminals worked fine even with the TV plugged in.[/QUOTE]
Forgot to say that I;ve also tried it in 16bits mode.  Now gonna try without X,

---

### Post by ashrack on 2006-02-02
here are my results:
with the current kernel which I compiled my self and removed lots of options from it(apperantly to much) and integreated support for SUSPEND2, VGA=0x317 gives a blank screen. Even if X isn't set to start automaticly.
So then I tried it with the default breezy kernel and VGA=0x317 works great.
Apperantly I am off to compiling another kernel...

---

