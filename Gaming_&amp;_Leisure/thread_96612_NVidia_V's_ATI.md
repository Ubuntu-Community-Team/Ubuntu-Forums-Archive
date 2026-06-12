---
title: "NVidia V's ATI"
date: 2005-11-29
forum: Gaming &amp; Leisure
---

### Post by MarkUK on 2005-11-29
Well its been a month or so since i switched from windoze XP to Ubuntu 5.10 and i must say its incredible , had a few problems but i got suck in and mamaged to overcome them with ease (Pulled a few hairs out)

Now , i have in my PC an ATI RAD 9800 Pro AGP but i have been hearing that the Nvidia cards are much better for ubuntu ! is this correct , the reason is since installing and getting games such as UT2004 and Quake4 etc running they seem a little bit choppy , it doesn't bother me that much as i don't realy play them for more that 2 hours a week , but saying that it would be nice to have a smooth game play .

Would i be better off tucking the ATI in a box somewhere and investing in a Nvidia card for better performance ?

P.S Latest ATI driver installed

Cheers
Mark

---

### Post by frodon on 2005-11-29
For sure nvidia cards works better in linux because nvidia provides itself the drivers so yes you will have a better support with nvidia cards.
However ATi drivers are not so bad and have the advantage to be open source (more in linux spirit).
So if you want to by a graphic card and if performances are important for you, it would be better to by a nvidia card, it's just my opinion ;)

---

### Post by Miguel on 2005-11-29
Hi Mark

**Short answer:** 

I wouldn't ditch the 9800 pro unless I were going to replace it anyway or if I really needed better performance.

**Long answer:**

The truth is that nVidia's drivers are better than ATi's. How much? The difference will probably be the same as in Windows before the Radeon 9000's.  Is the difference in performance important? Probably, but surely it is not critical (unless your fps drop below 30). But I can't really tell you how large the difference is, since I don't have a linux system with an nvidia card currently. 

If you are still dual-booting, it probably is a better idea to boot into windows to play than buying a new video card... unless you were already thinking to upgrade your video card.

However, if I bought a new video card, it would be an nVidia? Why? Because of their linux drivers. Currently, a hardware accelerated desktop (windows casting shadows, transparence effects, fading windows and faster redraw) is only practical if you own an nVidia card (yes, a fx5200 matches or outperforms a X850PE in 2D with their current drivers) or an ATi 9200 (the last with opensource driver).

Hope it helps,

Miguel

---

### Post by Miguel on 2005-11-29
[QUOTE=frodon]
However ATi drivers are not so bad and have the advantage to be open source (more in linux spirit).
[/QUOTE]

As I posted above, ATi drivers used to be open source until the 9200 (included). Later ati cards need propietary drivers for 3d hardware acceleration.  

As a sidenote, latest X.org (7.0RC2) contains experimental (non ati) open source drivers for the 9550's and above (9*00 series maybe??). They sure can't be much worse than the propietary ones... and they are free.

---

### Post by MarkUK on 2005-11-29
[QUOTE=Miguel]Hi Mark

**Short answer:** 

I wouldn't ditch the 9800 pro unless I were going to replace it anyway or if I really needed better performance.

**Long answer:**

The truth is that nVidia's drivers are better than ATi's. How much? The difference will probably be the same as in Windows before the Radeon 9000's.  Is the difference in performance important? Probably, but surely it is not critical (unless your fps drop below 30). But I can't really tell you how large the difference is, since I don't have a linux system with an nvidia card currently. 

If you are still dual-booting, it probably is a better idea to boot into windows to play than buying a new video card... unless you were already thinking to upgrade your video card.

However, if I bought a new video card, it would be an nVidia? Why? Because of their linux drivers. Currently, a hardware accelerated desktop (windows casting shadows, transparence effects, fading windows and faster redraw) is only practical if you own an nVidia card (yes, a fx5200 matches or outperforms a X850PE in 2D with their current drivers) or an ATi 9200 (the last with opensource driver).

Hope it helps,

Miguel[/QUOTE]

**If you are still dual-booting**

No i switched completely to Ubuntu (sick of windows)

**unless you were already thinking to **

I was thinking of upgrading to PCI Express after christmas (money and wife permitting :razz: )

For now i think i'll stick to the ATI untill that time comes 


P.S on another note , once games are installed they don't leave any desktop shortcuts , this isn't a problem as i just create a new one BUT where do all these icons (like the UT2004 windoze desktop icon) come from as i cant seem to select one within Ubuntu to use.

Cheers
Mark

---

### Post by Miguel on 2005-11-29
Then, Mark, don't doubt it. Have a look at the hardware forums for a troublesome kernel-nVidia drivers combination (just in case) and go for it. 

On the icons note... I usually look for small images in the directory of the game. If there isn't one, you can always take a screenshot of the main menu and resize it. Assigning the images to the shortcuts would then work.

PS: Maybe the "lamb's eyes' technique" works also with your wife (at least it can make her laugh)

PS2: Remember you will have to reconfigure your X server after changing the video cards!!!

---

### Post by MarkUK on 2005-11-29
Many thanks for all your input .

I'll have a look around the directory later , as i do remember seeing one , but this was an xlm <-- or something simular but it would'nt let me use it . Might see if i can convert to png later 

Cheers
Mark

---

### Post by leech on 2005-11-29
There is a ut2004 icon set up in the menu, the strange thing is, sometimes for me it puts it under "Other" on the main applications windows.  Or if I have the 'menu' package installed, it creates a menu entry in the debian style, which will give you a games menu, and it should be at the bottom of that (this has worked for me with Postal2, UT2004, UT2003, UT, Unreal Gold, Doom3 and Quake4)

Leech

---

