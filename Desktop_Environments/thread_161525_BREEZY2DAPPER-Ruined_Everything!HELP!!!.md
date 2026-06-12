---
title: "BREEZY2DAPPER-Ruined Everything!HELP!!!"
date: 2006-04-17
forum: Desktop Environments
---

### Post by krait on 2006-04-17
Here s what happened-:

i wanted to move from breezy 2 dapper, so i changed the sources.list file.at first i jus wanted Xorg7.0 and the latest kernel, so just upgraded those 2. but i wasnt able to log in using the new kernel, Xorg seemed to have got upgraded tho.then i figured, upgrading fully might be a good idea,so did 
sudo apt-get dist-upgrade
tht dint seem to do anything.so i went to synaptic and upgraded all files thro tht.at 1st, only 500 or so out of 700 packages got upgraded.then i restarted and started upgradin the remainin 200.i went off fr a while and came bak to see my screen blank.mouse clicks,keypad nothing changed tht.So i jus turned off power and restarted.then i logged in using the old kernel(2.6.12-386,686 gives seg fault) only(new one doesnt work,screen stays blank after selection),to find some things upgraded.but now, my networking(both my network interfaces(eth0 and eth1) and a whole lot more are out of order.tht means i cant connect to the net and possibly upgrade or anything.so thts my  situation.

i dont wanna reinstall ubuntu(all those hrs spent on configuration of ubuntu](*,) ).i could really appreciate some quick help.

:( :-?

---

### Post by mips on 2006-04-17
Hopefully someone can help. 

If it was me I would backup my data & simply do a fresh install of the latest dapper build. Should not take that long to configure your system.

---

### Post by Jaygo333 on 2006-04-17
[QUOTE=krait]Here s what happened-:

i wanted to move from breezy 2 dapper, so i changed the sources.list file.at first i jus wanted Xorg7.0 and the latest kernel, so just upgraded those 2. but i wasnt able to log in using the new kernel, Xorg seemed to have got upgraded tho.then i figured, upgrading fully might be a good idea,so did 
sudo apt-get dist-upgrade
tht dint seem to do anything.so i went to synaptic and upgraded all files thro tht.at 1st, only 500 or so out of 700 packages got upgraded.then i restarted and started upgradin the remainin 200.i went off fr a while and came bak to see my screen blank.mouse clicks,keypad nothing changed tht.So i jus turned off power and restarted.then i logged in using the old kernel(2.6.12-386,686 gives seg fault) only(new one doesnt work,screen stays blank after selection),to find some things upgraded.but now, my networking(both my network interfaces(eth0 and eth1) and a whole lot more are out of order.tht means i cant connect to the net and possibly upgrade or anything.so thts my  situation.

i dont wanna reinstall ubuntu(all those hrs spent on configuration of ubuntu](*,) ).i could really appreciate some quick help.

:( :-?[/QUOTE]

I also tried to do the same thing. Now I'm stuck with the same errors you have. Somebody told me to unistall ubuntu-desktop then reinstall it. I removed it, but when I try to reinstall it, it keeps telling me that I need about two hundred other apps upgraded. I try suo apt-get upgrade *.* but that doesn't seem to work. I'm now stuck reistalling everything from scratch. sudo apt-get install *.* It seems to work, been doing it for some time. But the thing is, for every app I install, I remove about ten others.

This has been a bad a idea from the beginning. I just wanted to install XGL, not crash my distro. 
Just wanted to tell you, you are not alone in this long struggle.

:ph34r: Jaygo33 :ph34r: 

P.S.](*,)Immediately I upgraded the distro and restarted my pc, Xserver crashed](*,) .
Been trying to fix it ever since. Been doing everything from Terminal. GDM won't start. tried reinstalling xorg, but ](*,)
At least putty will work. Trying to do everything remotely with help from other people who, for somegoddamn reason, have managed to get it to work right.

Oh Well, good luck to everybody.

---

