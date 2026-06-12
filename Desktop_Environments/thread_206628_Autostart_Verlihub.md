---
title: "Autostart Verlihub"
date: 2006-06-30
forum: Desktop Environments
---

### Post by Exergy on 2006-06-30
Hello, ive successfully installed verlihub (a dc++ server) and had it running for a while now, however im having trouble getting it to start at startup, currently im  having to manually start it each boot. With the verlihub official forums being down, I figured I would ask at the next best place, here :)

Obviously ive searched, and it did bring up results, most noticably:

[http://ubuntuforums.org/showthread.php?t=200443&highlight=verlihub](http://ubuntuforums.org/showthread.php?t=200443&highlight=verlihub)

Which I followed carefully, but no joy, I must add that this method works for all other scripts ive tried, but just not Verli?

Am I missing something, also im actully using ubuntu 5.10, thought I couldnt find the relevant section, dont believe it will make much difference in this case?

Thanks for the help.

---

### Post by SteffJay on 2006-10-16
Yes, it does make a lot of difference as to what distro you use. I have since moved on from Ubuntu v5.10 to v6.06 Dapper / Drake and what i wrote in your link, no longer applies in my case, so i am stuck again. If you have managed to get it working, please let me know how you managed it. The only thing i would say is, after doing what i said in the link, Verlihub will only autoboot if i log out of my account and into root :confused:  (strange but true). Hope this helps !!

---

### Post by Trazan on 2006-10-22
Dunno if this is gonna help you...but I added it to sessions and it starts right away](*,)

---

### Post by SteffJay on 2006-10-22
I tried that but i used /etc/init.d/verlihub but it still did'nt work even after a reeboot.....  :(

---

### Post by gostyuk on 2007-05-27
cd /etc/init.d

sudo vim verlihubb

//and write there this script

#!/bin/sh
sudo vh_runhub
place_here_your_root_password


//afret you write here the script do as sudo: sudo update-rc.d verlihub defaults
//reboot your computer :D

---

### Post by Meserias on 2007-11-22
Can someone please help me with the necessary commands to autostart on boot on Ubuntu 7.10 Verlihub ?
Please help me with this...because I can understand that I miss :confused:
Thank you

n00b user

---

