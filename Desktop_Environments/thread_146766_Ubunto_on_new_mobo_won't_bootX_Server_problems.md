---
title: "Ubunto on new mobo won't boot/X Server problems"
date: 2006-03-18
forum: Desktop Environments
---

### Post by rjay3 on 2006-03-18
I replaced a fried mobo on a pc, slid in Ubunto (in a HD case) and it started loading the modules but then I got the errors:"Failed to start the X server. It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" I click YES. The next diaglog boxes give me the system version, release date, build, current OS, module  Loader present, etc. Next box asks me if I would like to view the detailed X server output, I click yes again and it's pretty much the same info. The last box states that "The X server is now disabled. Restart GDM whe it is configured correctly.  I click ok and I'm presented with the black terminal screen and to login. I can't login with the one and only password I use for Ubunto. 
I switch to Mepis1 3.4.3(in another HD Case) and it has no problems booting up whatsoever! 
I put in Ubunto as "slave" and can see and access all my directories and files(hdb1).
I also have WinXP Pro in another slide-in HD Case and except for having to do a Repair/Install there's no problem. Can someone please help me figure this out? As an addendum, when I had Ubunto working with the other mobo I noticed that the jumper was always in the 'slave' position and when I tried it as 'master' it wouldn't boot at all!!

---

### Post by IYY on 2006-03-19
Are you still using your old video card, or was it integrated in the motherboard? If it was, you'll need to reconfigure your xorg.conf file to fit your new video card

---

### Post by rjay3 on 2006-03-19
I'm using my old video card, a Radeon 7000, after first trying the built-in video on the new Octek rhino ATIA 3-ASE motherboard. If I do have to reconfigure my  
xorg.conf file, how do I get in if I'm unable to login?
Thanks for the reply

---

### Post by IYY on 2006-03-20
If you switched your video card, you will most certainly need to reconfigure xorg.conf. You don't need X to login, you should still be able to login using your username and password.

---

### Post by bluevoodoo1 on 2006-03-20
login and type...

sudo dpkg-reconfigure xserver-xorg

that might get you going. 

to manually edit your xorg.conf from the command line...

sudo nano /etc/X11/xorg.conf
Ctrl+o to save
Ctrl+x to quit

---

