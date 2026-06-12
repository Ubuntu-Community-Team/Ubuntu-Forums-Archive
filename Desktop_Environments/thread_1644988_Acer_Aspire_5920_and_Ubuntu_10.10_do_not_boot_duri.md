---
title: "Acer Aspire 5920 and Ubuntu 10.10 do not boot during power on"
date: 2010-12-14
forum: Desktop Environments
---

### Post by nagarajusreeram on 2010-12-14
Hi,
 
I was using Ubuntu 10.04 for the last 6 months, recently I have upgraded to Ubuntu 10.10, it worked fine for around four days, Now the problem is When I power up the system using power button, the system do not power up, I tried to boot from cd both Ubuntu and Windows XP, none works, I tried to go to BIOS setup using F2 and F12 (Acer Aspire 5920 model laptop), but i could not, just a blank display appears, here are some symptoms:
1. When powered on - LED indicating pocressor operation glows for a moment and disappears, few other LEDS indicating batter, music play, forward,stop LEDs glows as as usual, 
2. Only blank screen appears
3. tried to switch on the wifi and bluetooth buttons, both did not glow indicating it is not working.
4. Paculiar thing is this symptons appears first time, suddenly all stop glowing and after 2 to 3 seconds again the system comes to this state and remains forever.
 
Questions:
1. Is it possible to be hardware problem ?
2. If it a software problem the suspect can be Ubuntu 10.10 version? 
 
Can any one help on how to debug this problem

---

### Post by plux on 2010-12-14
Most likely it's a hardware problem. Could be the 'Black screen of death' problem which affects many notebook with Nvidia GPUs build around 2008. I have a HP notebook with a similar problem.

[http://apcmag.com/nvidia_disaster_thousands_of_gpus_faulty.htm](http://apcmag.com/nvidia_disaster_thousands_of_gpus_faulty.htm)
[http://www.theacerguy.com/forum/topic/acer-aspire-5920-black-screen-of-death-help](http://www.theacerguy.com/forum/topic/acer-aspire-5920-black-screen-of-death-help)

---

### Post by nagarajusreeram on 2010-12-14
Thanks for reply, I tried several times pressing power button followed by pressing F2, suprisingly I was able to log into my user profile just for one time, but before preparing my self to back up my files, I was automatically logged out, displaying error message, but could not capture the message, error saying /extra....... , and it shut downed, I agained several times but no use, Is there any way to enter into the boot manager other than F2 and F12, I will try again and would post any progress, guide for any further steps

---

### Post by nagarajusreeram on 2010-12-17
Thanks for replies, I got my laptop serviced,  found it to be harddisc problem. Now I changed the harddisc  and enjoying with laptop

---

### Post by BryanMtdt on 2010-12-17
I'm glad you could get it to work, T don't know alot about laptops hardware but write that you couldn't enter BIOS by F2? I'm curius on the HDD affecting the BIOS load.

---

