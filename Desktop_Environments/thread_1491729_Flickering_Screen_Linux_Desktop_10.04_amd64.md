---
title: "Flickering Screen Linux Desktop 10.04 amd64"
date: 2010-05-23
forum: Desktop Environments
---

### Post by harisv339 on 2010-05-23
Hello,
I am trying to install Linux Desktop 10.04 amd64 onto my machine. 
CONFIG: Intel q9550 @ 3.40 GHz, 8GB DDR2 1066 RAM, 1TB HDD, Sapphire ATI Radeon HD4670 with 1GB DDR3 VRAM, Win 7 x64 installed.

First burnt a graphical installer for Linux v10.04, then attempted to install - the GUI that loaded for installation caused my screen to flicker every 1 second going on and off. The picture was never stable, and so I had to reset the machine and abort.

I tried burning the alternate installer for 10.04, everything installed clean using Text Interface, but upon restart and while the GUI loaded, the flicker recurred and the linux remains unusable.

If anyone has any experience getting past this problem, pls enlighten; Much appreciated !

---

### Post by proggy on 2010-05-24
I also had that flickering (i`d say less than a second) with the live cd install so i did an upgrade from 9.10 to 10.04 and it worked fine.
I f you don`t have an ISO image file of 9.10 you can get it here 
 [http://cdimage.ubuntu.com/releases/9.10/release/](http://cdimage.ubuntu.com/releases/9.10/release/)

---

### Post by ndorphine on 2010-05-25
I had the same problem with a PowerColor 4870 Radeon, it turned out that the memory clock on the card was overclocked, I used 
```
/usr/bin/aticonfig --od-enable
```
and then
```
/usr/bin/aticonfig --od-setclocks=0,900
/usr/bin/aticonfig --odgc
```
Although you'll most likely want to use different clock speeds for your 4670

---

### Post by harisv339 on 2010-05-25
Ndorphine - I 'm quite a newbie to configuring hardware on Linux ... however I guess overclocking might be whats bothering the graphics. I 've pushed my q9550 from its stock 2.83 GHz speed to 3.40 GHz. I didnt bother to study its effects on the graphics card (left the math to Gigabyte's Easy Tune 6!) but my BIOS does show that the Graphics Card (HD4670) is operating in its normal settings. 
 
I will be trying out the aticonfig command shortly. Will post back if it worked the magic ~! Thanks again !

---

### Post by proggy on 2010-06-01
> **harisv339 said:**
> Hello,
I am trying to install Linux Desktop 10.04 amd64 onto my machine. 
CONFIG: Intel q9550 @ 3.40 GHz, 8GB DDR2 1066 RAM, 1TB HDD, Sapphire ATI Radeon HD4670 with 1GB DDR3 VRAM, Win 7 x64 installed.

First burnt a graphical installer for Linux v10.04, then attempted to install - the GUI that loaded for installation caused my screen to flicker every 1 second going on and off. The picture was never stable, and so I had to reset the machine and abort.

I tried burning the alternate installer for 10.04, everything installed clean using Text Interface, but upon restart and while the GUI loaded, the flicker recurred and the linux remains unusable.

If anyone has any experience getting past this problem, pls enlighten; Much appreciated !
I f you are able to install Ubuntu you need to install the propriatary drivers from ati it will solve the problem guaranteed

---

### Post by harisv339 on 2010-06-05
Proggy,
Here is what I did so far and my observation thereon - 
Downloaded Ubuntu 9.10 Desktop edition and I was able to install it successfully. No flickers and everything looks clean. I did not alter any of my overclock settings and everything seems perfectly stable. Also, the driver auto update kicks-in and recommends the upgrade to ATI proprietary drivers and updating it worked clean as well.
 
But from the auto OS upgrade feature within 9.10, I tried upgrading to 10.04 and everything went well until it restarted. Once it restarted, the screen flicker got back in and I am now back to square one :-( I would like to try updating the drivers in the 10.04 install I have in place now. Please tell me if there is a way I can escape the GUI mode, get into the shell, update the ATI driver, then reboot back into GUI and see if that solves the problem. Please help me with necessary commands if possible...

---

### Post by owepia on 2011-06-19
Hi,
I am a newbee. After having installed Linux 9 LXDE I immediately had a problem.  The screen was flickering.  I don't know how to enter code yet, so I looked for another solution.  Go to preferences, then monitor settings.  Once there set the refresh rate to 60.  I don't know if this will work for every Linux configuration, but it worked for me...no more frustration.

---

