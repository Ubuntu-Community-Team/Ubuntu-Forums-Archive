---
title: "Americas Army his a ....problem?"
date: 2006-05-31
forum: Gaming &amp; Leisure
---

### Post by cobbweb on 2006-05-31
Hey, 
  I very new to gaming with Linux, but I wanted to play a game called Americas Army. I played it on Windows and really like it, however, I would like to like playing it on Ubuntu Linux. I downloaded the latest Linux version and installed it. That went fine, however, I now have a problem on startup. When I try to start the program (sh armyops) it starts to run and goes through the following.... 
-----------------------------------------------------------

Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error
-----------------------------------------------------------

The program then just stops and won't load. I don't know what a GLX visual is and am not sure how to fix it, but I figured others in the Linux Gaming Community have most likely ran across this problem before and fixed it. How would I fix this problem? It's really quite agrivating as I wanna delete my Windows partion and this is the only real thing holding meback. (I finally found a Linux Flash Editor) Any help is more than wanted. 

 Mahalo, 
 Konacoffeeguy

---

### Post by meng on 2006-05-31
It would help I think to know what video card you are using and whether or not you did anything to configure 3D acceleration with it.

---

### Post by cobbweb on 2006-05-31
Oh Right... 
 
 Ok so I have a ATI 9600 and I have not done anything to configure 3D acceleration. However, the box did say it's 3D enabled. 

Cobbweb

---

### Post by meng on 2006-05-31
The box? You mean the box the graphics card came in? :)

I have no personal experience with ATI on Linux, but I suspect you'll need to get your hands dirty to enable 3D acceleration. Have a look here:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

and please let us know how it goes.

---

### Post by cobbweb on 2006-05-31
The instructions are for Dapper(the easiest ones at least) so Im ganna wait until tomarrow when i can upgrade to dapper. Ill tell you how it goes tomarrow... 

 Cobbweb

---

### Post by Lord Illidan on 2006-05-31
[quote=cobbweb]The instructions are for Dapper(the easiest ones at least) so Im ganna wait until tomarrow when i can upgrade to dapper. Ill tell you how it goes tomarrow... 

 Cobbweb[/quote]

You can update to Dapper now... skipping the rush, hehe.. Seriously, 2morow, the mirrors are going to be flooded.

---

### Post by cobbweb on 2006-05-31
wait, I can update to Dapper!? Is it going to be the same Dapper that will be posted tomarrow? Also, how do I upgrade to it without deleting all the stuff on my computer?? 

Cobbweb

---

### Post by deathbyswiftwind on 2006-05-31
Yeah Id upgrade  to dapper download fglrx from the repos and youll be set. Your 3d wasnt enabled (at least enables properly) but anyways do that and get on aa. I prefer the jkl server or MOD server. Both are good.

---

### Post by R3linquish3r on 2006-05-31
Side note: When you install it you don't type "sh armyops" to run it just type "armyops" :)

---

### Post by cobbweb on 2006-06-01
When I just type armyops it gives me this and doesn't start

bash: armyops: command not found

---

### Post by cobbweb on 2006-06-01
[QUOTE=meng]The box? You mean the box the graphics card came in? :)

I have no personal experience with ATI on Linux, but I suspect you'll need to get your hands dirty to enable 3D acceleration. Have a look here:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

and please let us know how it goes.[/QUOTE]



AHH ok I copy/paste the instruction in the terminall and rebooted. That is where the big problem came. The screen now just flashes and says "Out of Range" I can't seem to long in as before in a GUI at all. I tried recovery mode and It takes me to just a command line log in. I think i will have to some how get it to work that way, but it is kinda scaring me. I don't wanna loose my desktop. How do I fix this ??? eeek 


 Thanks 

 ha

Cobbweb

---

### Post by eqisow on 2006-06-01
It would seem your monitor is now trying to display a higher resolution/refresh rate than it is capable of. You probably selected the wrong max resolution when you went though the fourth step. To fix this, boot into 'recovery mode' and enter *sudo dpkg-reconfigure xserver-xorg*. Make sure you choose fglrx as your driver. Also, when asked about your max resolution, choose 'SImple' from the Simple/Medium/Advanced options. It will ask for your screen size. After that it configured, simply Reboot. You should now be able to log into your fancy new 3D enabled desktop.

Good luck!

---

### Post by cobbweb on 2006-06-01
[QUOTE=eqisow]It would seem your monitor is now trying to display a higher resolution/refresh rate than it is capable of. You probably selected the wrong max resolution when you went though the fourth step. To fix this, boot into 'recovery mode' and enter *sudo dpkg-reconfigure xserver-xorg*. Make sure you choose fglrx as your driver. Also, when asked about your max resolution, choose 'SImple' from the Simple/Medium/Advanced options. It will ask for your screen size. After that it configured, simply Reboot. You should now be able to log into your fancy new 3D enabled desktop.

Good luck![/QUOTE]

I love you man, You saved my computer. Thanks I got to my command line and typed 

fglrxinfo

and got 


Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


I believe this means it is installed, however when I try to play AA it gives me the same error as my first post. Ah! I think it has something to do with the "extension "XFree86-DRI" mission on display" part. Have any idea what that is.? Also thank you so much for the help. 

 Cobbweb

---

### Post by eqisow on 2006-06-01
For posterity (problem solved on AIM):

X.org was still using the "ati" drivers. We manually edited the xorg.xonf file with *sudo gedit /etc/X11/xorg.conf* (kwrite instead of gedit for kde) and changed the line *Driver "ati"* under *Section "Device"* to *Driver "fglrx"*. The computer then needed a reboot. Ctrl + Alt + Backspace did not work.

After this, fglrx has the following output:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Generic
OpenGL version string: 2.0.5755 (8.24.8)
```

America's Army now works.

Note: I assume that the ati driver was still in use because fglrx was not properly selected during *sudo dpkg-reconfigure xserver-xorg*. As such, it should be noted that you have to use space to select the driver (and other options), not enter.

---

### Post by cobbweb on 2006-06-01
problem solved, I needed to reboot my system. AA works just fine now, infact its the best game play i havee ever had. No lagging, greate graphics. I don't know why i didn't switch to Linux earlier... ah its so freakin awsom. Way better than a windows machine. Just can't get over it . Dapper rocks... cobbweb out ...

 mahalo

---

### Post by Antal on 2006-06-02
Good to hear you got it sorted and you're up and running!!

I'm playing a lot of AAO and will be going to the new dapper release with AAO soon :eek: 

So you out there soldier! Hooah!

---

### Post by meng on 2006-06-02
Hey cobbweb I'm glad your persistence paid off (with some extra assistance over AIM).

---

