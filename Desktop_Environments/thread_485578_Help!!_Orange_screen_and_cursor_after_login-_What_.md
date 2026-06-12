---
title: "Help!! Orange screen and cursor after login- What happened??"
date: 2007-06-27
forum: Desktop Environments
---

### Post by SkySpeedr on 2007-06-27
My Ubuntu 6.06 has been working fine for months but tonight I reboot and login and all I get is a big orange screen with a movable cursor on the screen!! Login seems normal but I just never get to the desktop!  I looked at another post and for a similar problem and they suggested stopping X and running dpkg-reconfigure xserver-xorg, which I did but all that has done is reset my screen size to 1024x768 (I had previously edited xorg.conf to set it to my monitor size of 1360x768).  

How do I get my desktop back??  Pleeeeaaassseee... I don't want to have to reinstall and re-do all the stuff I've spent months configuring!! 

ASUS M32N-SLI MB
AMD64 dual core (Using i386 version of Ubuntu)
1Gb RAM
320Gb SATA
NVIDIA 7300GS

Thanks!!!!

---

### Post by CaveRat on 2007-06-27
Seems like this problem is very random yet very annoying. I searched for answers myself and found none after my Feisty (twice) *and* Gutsy borked in this manner. Is there anyone in this forum that can give us an idea of what is causing this odd behavior? Is there some glitch in  nvidia-glx-new that could cause this by chance or something else we are doing?

---

### Post by SkySpeedr on 2007-06-28
I don't know if this has anything to do with it but I was thinking back to just before this happened and I remember picking up my keyboard and accidentally hitting the "sleep" button.  After that the system was unresponsive. I think the orange screen came up then but I'm not sure.  Anyway, I rebooted and logged in and got the orange screen. 

It's not quite dead, tho. I discovered that ATL+PrintScr causes the save print dialog to come up and I can close the dialog, but that's about it as far as desktop functionality. 

I'm dead in the water, so any suggestions anyone could give would be greatly appreciated!

---

### Post by SkySpeedr on 2007-06-29
So how do I uninstall X and reinstall it at the CLI?  I can't think of anything else I can do!!

---

### Post by SkySpeedr on 2007-06-30
Does anyone have experience re-installing X/Gnome without reinstalling the whole OS?

---

### Post by SkySpeedr on 2007-07-01
I took a wild guess and I was right.  Based on something I saw in another post I ran **sudo apt-get install gnome** and I'm back in business!  Obvious when you think about it!! :D

---

### Post by bigoeprm on 2007-07-25
I had this same problem, but (re)installing gnome (as the previous poster suggested) worked! I believe I got this problem because I removed all power management stuff from my machine. Apparently disabling power management's going to be tougher than that...

---

### Post by xaviesh on 2008-04-17
Hello,
     I am seeing the same problem and I'm not sure how to input the command "sudo apt-get install gnome" as I cannot open any terminals in Ubuntu (the menu is not available). Please help as I'm stuck and I do not want to re-install...

Shakila

---

### Post by Jota37 on 2008-05-18
> **xaviesh said:**
> Hello,
     I am seeing the same problem and I'm not sure how to input the command "sudo apt-get install gnome" as I cannot open any terminals in Ubuntu (the menu is not available). Please help as I'm stuck and I do not want to re-install...

Shakila

Hi,

To see a terminal, you'll have to press (at the same time) Control-Alt and one of the F1-F6 keys (any one). You can log in to up to 6 terminals that way. Ctr-Alt-F7 gets you back into the graphical part.

I hope I was clear.
Cheers
J

---

