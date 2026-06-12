---
title: "dialup and music/video"
date: 2006-07-13
forum: Desktop Environments
---

### Post by Fittersman on 2006-07-13
alright i dont know what to do anymore about dialup.... i tried using gnome-ppp-0.3.23.tar.bz2 and it told me that there is not valid C in %path or something like that and it just quit, ive tried using scan modem on breezy but not yet on drapper.

does anyone have any suggestions here??      (](*,) <---me)

and about the music and video when i try and load a song from my windows partition it says somethign about the file is encripted, how can i play my songs?

and again for the internet, what if i used wine to go into the windows partitoin and loaded my internet from there? (i dont have wine so i cant try it but if that might work ill get it...)

---

### Post by derakhshani on 2006-07-13
Currently I am using gnome-ppp. It is perfect. 
It is better to use synaptic (Ubuntu package manager) to find programs and install them therefore do not find source code by yourself when there is the same package in synaptic.
```
sudo synaptic
```
if you did not use synaptic before take a look at:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_apt-get_the_easy_way_.28Synaptic.29]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_apt-get_the_easy_way_.28Synaptic.29")
gnome-ppp is only a dial up program, it does not install your modem for you. first be sure modem is recognized by Ubuntu. Usually external modems are recognized easyly by pluging to pc but bultin modems (winmodems) are not, (personally I have a laptop whose modem is builtin I found its driver from somewhere else after that gnome-ppp works with modem).

about encryption I did not understand which error you have received.
I guess two possibilities:
1. Ubuntu Desktop by default does not have some audio decoders like mp3 and wma (becuase of license issues) therefore you should install these decoders to be able to listen to your music files in mp3 or wma or ... format. 
take a look at:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs")
2. if you can not access special directories in your windows partitions maybe partitions of these directories are ntfs and from windows you enable encryption option for those directories. if it is true to be able to access them from linux you should disable this encryption option from windows.

up to now wine is not a perfect program. It cannot run a lot of windows programs. Firefox is better than IE, use it instead of IE.

---

### Post by Fittersman on 2006-07-14
thanks and by the wine thing i meant load the internet through it, not the browser (as in the program that starts the dialing)

but thanks ill try your stuff

and how about the gnome-ppp thinger, why does it say that error? (i cant remember what it was but its up on my first post :P)

---

### Post by utnubu001 on 2006-07-14
yeah i had that problem too
but wvdial is really faster than gnome-ppp

---

### Post by utnubu001 on 2006-07-14
oh and about ur vid/music problem
install XMMS and Xine
Worked for me...

---

