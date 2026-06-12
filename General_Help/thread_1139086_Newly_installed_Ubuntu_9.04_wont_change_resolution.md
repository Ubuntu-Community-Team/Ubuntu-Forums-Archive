---
title: "Newly installed Ubuntu 9.04 wont change resolution, has graphics problems and crashes"
date: 2009-04-26
forum: General Help
---

### Post by Leopardson on 2009-04-26
I installed Ubuntu 9.04 on my hard drive, completely overwriting my Windows XP. 

Note: Windows ran fine, except for the fact that it is Windows.

System:
Ubuntu 9.04, completely overwrote Windows XP  (Doubt that is relevant).

ATI Radeon HD 3650 W/ Latest catalyst drivers **from the ATi website.** No problems when I had Wincrap.

1GB DDR Ram, memtested twice, no errors.

100GB IDE Hard drive, no past problems. 

AMD Sempron 3100+, no pas problems.

Resolution:
Everything was fine at first, I ran at 1600 x 1200, until I decided to change my resolution to 1280 x 960 to improve compiz performance.
It asked me to log in and out, so I did. 

When I came back, it was 1024 x 768 with 2-inch black borders.
It is stuck this way, unless I change the resolution to 1024 x 768 in which case it goes fullscreen.

Basically, I'm stuck at 1024 x 768, or 1024 x 768 with 448 black pixels as a border.

Graphics problems:
-When I start anything in wine, the screen blinks with black boxes on the screen for about two minutes, works fine for about three minutes, then crashes. I got Wine from Synaptic.

-When I play World of Padman (Linux edition), the game works for about 15 minutes. After that, it goes to windowed mode, still runs with some graphical glitches on screen, though it still appears to be running at normal FPS. It disables my keyboard and mouse, requiring me to use the restart button on my tower.

-When I play Hitman :Blood money (Wine), it crashes after a few seconds, even though it works fine on my friend's Ubuntu 8.10 system.



I have tried turning the effects off of Compiz, restarting, and reinstalling video drivers.
I installed Ubuntu hoping it would run better then my POS Windows did. So far, it isn't. :(
(Windows ran bad because of some nasty spyware, not due to any hardware problems that should affect Ubuntu.)

Will someone please help?

---

### Post by cmost on 2009-04-26
Have you tried using the catalyst driver available in the repositories rather than the one from ATI's (AMD's) website?  You know how Ubuntu is...more and more like Windows.  It tries to do everything for you and misses the boat if you actually do something for yourself.  In my case, when I removed the Nvidia driver from restricted hardware modules and compiled my own (newer version) from nvidia's website, Ubuntu behaved as if NO proprietary graphics driver were installed and defaulted to a very low resolution upon reboot.  This issue is made worse by the fact that xserver 1.6 no longer requires an xorg.conf file (which was reset to an extremely brief generic version upon removing Synaptic's version of the nvidia driver.)  I had to manually edit the xorg.conf file and re-copy several key sections (including driever = nvidia, in my case) from a backup copy in order to restore full functionality.  I hope you have a recent backup of your xorg.conf file too.  Good luck!

---

### Post by Leopardson on 2009-04-26
Thanks for the reply!

I believe I have a xorg.conf file backed up, I'm not sure.
I am new to Ubuntu (not to Kubuntu, just the gnome edition). How do I install them from the repositories?

---

### Post by Leopardson on 2009-04-27
If there is an alternative to creating new posts like this to bring the thread up, I'd like to know it. I hate to have to retype the messages.

---

