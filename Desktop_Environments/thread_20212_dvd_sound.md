---
title: "dvd sound"
date: 2005-03-15
forum: Desktop Environments
---

### Post by clb137 on 2005-03-15
Hi anyone,

I know from reading the threads that a lot of people are having problems with DVD playback and sound, as well as the quality of the playback, I have a solution it is not ideal but if you want to watch a dvd it does work.  Please be aware I am not a Linux guru.

After you have installed the files for DVD playback see the guide 4.10, then you need  to create a .sh file with 'gedit' or something like. In this file I put the following, 

sudo hdparm -d 1 /dev/hdc

killall esd
 
gxine

then save the file, something like 'dvd.sh';   open a terminal go in to the directory you saved the file in and 'sudo chmod -x dvd.sh, then type ./dvd.sh    gxine should start and all work well (sound and smooth dvd playback). 

the down side when you have watched your dvd you have to reboot to get your system sounds back.  not sure if this will help anyone, but i think that every little helps.  Any views or comments would be appreciated as I am only learning 

thanks

clinton

---

