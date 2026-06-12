---
title: "Firefox slow to refresh when moved"
date: 2005-11-16
forum: Desktop Environments
---

### Post by l.tambiah on 2005-11-16
If i have a firefox browser open and another firefox window open on top, i am finding that on moving the browser window (the one on top) around it seems to be rather slow in updating or refreshing the screen. I also notice that when i minimise a window too the black box effect in gnome seems some what slower and jerky. This has not happened to me before. 

I am sure the graphics driver is fine, as open GL screensavers and games work fine. 

Is anyone else having this problem? If so what could be causing this.

Its quite hard to explain this problem, maybe screenshots would help. Which i will add when i get home later tonight if required.

---

### Post by Hairy_Palms on 2005-11-16
the problem is you either havent got your 3D drivers installed, or you have an ATI graphics card, atis 3d driver is awful at 2d acceleration.

---

### Post by l.tambiah on 2005-11-16
I have a NVIDIA card which has worked fine with Ubuntu in the past. It is a good card, and the screen savers (open gl ones) work fine. To be precise the card is NVIDIA 6800 LE. I have installed the drivers and the NVIDIA logo appears on startup. 

Perhaps removing the nvidia driver and reinstalling the driver may help, im not sure.

---

### Post by linkunderscore on 2005-11-16
I was having the same problems with firefox 1.0.7

I also have nvidia drivers installed...everything else works flawlessly (UT2k4). 

Firefox1.5 doesn't seem to have this issue.

---

### Post by l.tambiah on 2005-11-16
[LEFT]Perhaps its a flaw in the Ubuntu package of Firefox. I thought it might be just my installation, but you have confirmed there is some possible bug here. Although firefox 1.5 is out on Release candidate i would rather use the 1.07 for now. 

[I]I shall install 1.07 from the mozilla site and run firefox from my home directory and see if this changes anything. However can't do that just yet till i get home from work, at current im posting this from a horrible windows xp os. 


[/I][/LEFT]

---

### Post by l.tambiah on 2005-11-16
After a bit of investigation, i have found it has nothing to do with the graphics card driver. This is a firefox problem.

Lets say we load a firefox browser onto the desktop, we then open another browser window on top of the other browser window, if i move the browser whilst loading a web page the browser window below shows trails of graphics from your movements.  

I have installed the 1.5 version and this seems a lot better, so at current this is my workaround. 

Thanks for the replys

---

### Post by l.tambiah on 2005-11-17
The problem with firefox has also appeared on a review on the internet. Firefox seems to be using an awful amount of CPU proccessing power, draining the system. This needs to be addressed. Perhaps this thread could be made sticky.

See link [http://www.madpenguin.org/cms/?m=show&id=5557]("http://www.madpenguin.org/cms/?m=show&id=5557") 

This guy had same problem but got round the problem by installing 1.5 beta of firefox, i imagine 1.07 would be fine too as long as the official tar ball is installed from the mozilla site.

---

### Post by fuscia on 2005-11-17
no more than anecdotal evidence, but i notice less trouble with firefox when i use multiple tabs rather than multiple windows. i think you'll notice 1.5 being better and faster than 1.0.7. i much prefer the new options window and now, you can use the blackjapan theme.

---

### Post by l.tambiah on 2005-11-20
> no more than anecdotal evidence, but i notice less trouble with firefox when i use multiple tabs rather than multiple windows

Yes you are correct it is know more than ancedotal evidence. I have reinstalled breezy and have found the usuall 1.07 browser is now fine. 

It is proberly the result of other installed packages from universe on my previous setup.

---

