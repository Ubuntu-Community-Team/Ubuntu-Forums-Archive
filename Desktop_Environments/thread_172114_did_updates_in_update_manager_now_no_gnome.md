---
title: "did updates in update manager now no gnome"
date: 2006-05-08
forum: Desktop Environments
---

### Post by tennvols_69 on 2006-05-08
well i finially got my dual head stuff figured out  along with the 3d rendering and decided to do the default updates in update manager. after doing this all seemed well until i rebooted. then i got the bsob saying x could not start due to  no nvidia kernal. so i go check my  xorg.conf file and all is well there. tried to restart gdm  and still same thing so i do 

su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
 then Sh Nvidia-Linux-x86-1.0-8178.pkg1.run  run through that and choose not to let it config. and then i restart gdm. and it boots but one screen does not display and the other is fine.  so i go back and let nvidia driver configure my xorg. and restart gdm  same thing only one screen.  all was well before i ram update manager. i have no idea what it actuall installed  or how to roll it back to before.  or what might be causeing this. 3d accel still works though but now i only have one monitor and its the crappy crt not my lcd.  

 ive been messing with dual head for a bit and every time before i used the newest nvidia driver and did the updates before the config.  this last time i did the updates last and  did not use the latest drivers. but for some reason im betting all my problems were cause of the  update manager  updates not the nvidia driver.
 any help would be greatly appriciated cause im puzzled???

---

