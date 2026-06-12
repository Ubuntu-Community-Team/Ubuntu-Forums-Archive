---
title: "Super Mario Clone FX install help needed"
date: 2006-06-14
forum: Gaming &amp; Leisure
---

### Post by Omnios on 2006-06-14
Hi I tryed downloading Super Mario Clone FX as it was listed onm the Ubuntu Gaming Information Site but can not seem to get it to compile properly. There is supposed to be a precompiled package for X86 systems but can not seem to find that either. I would realy like to check this game out. Any help would be apreciated.

---

### Post by seth0x2b on 2006-06-14
The rpm packages are on the project's sourceforge page.
Just "sudo alien" them, install and happy play :). Start it with smc.x
[http://prdownloads.sourceforge.net/smclone/smc-0.96-jdsrX.4.i386.rpm?download](http://prdownloads.sourceforge.net/smclone/smc-0.96-jdsrX.4.i386.rpm?download)

Cheers

P.S. It complained about missing libSDL_gfx.so.13(I had libSDL_gfx.so.4, so I just did a  "sudo ln -s /usr/lib/libSDL_gfx.so.4 /usr/lib/libSDL_gfx.so.13" and it runs perfectly)

---

### Post by Omnios on 2006-06-15
Installed the rpm package with alian and did the link and every works fine. After trying this game any Mario fan will love this game :KS :KS :KS :KS :KS

---

### Post by hardingfele on 2008-06-03
hi,

am new to linux, so i may have made some obvious mistakes (though not to me) but it didn't work. took the rpm pre-comiled version and also managed to convert it to a .deb file and install it afterwards. think it worked:

me@me-desktop:/usr/local/games/SMC$ ls
data  levels  preferences.ini  savegames  screenshots  smc  smc.desktop  smc.x  smc.xpm  world
me@me-desktop:/usr/local/games/SMC$ smc.x
./smc: error while loading shared libraries: **libSDL_gfx.so.13: cannot open shared object file: No such file or directory**
me@me-desktop:/usr/local/games/SMC$ 

this is what i got when i tried to run it. i also looked for that libSDL_gfx.so13 file and found the libSDL_gfx.so4 only, so i did
"sudo ln -s /usr/lib/libSDL_gfx.so.4 /usr/lib/libSDL_gfx.so.13", but not quite understanding what it actually does ;-/. 

do i still have to change permissions somewhere? 
permissions for the libSDL files:
lrwxrwxrwx  1 root root       20 2008-05-26 21:40 libSDL-1.2.so.0 -> libSDL-1.2.so.0.11.1
-rw-r--r--  1 root root   420376 2008-01-05 05:52 libSDL-1.2.so.0.11.1
lrwxrwxrwx  1 root root       24 2008-06-03 12:06 libSDL_gfx.so.13 -> /usr/lib/libSDL_gfx.so.4

i also set the /lib and /usr/lib as a PATH. maybe unnecessarily...

would love to play ;-D 

thx a lot!

---

### Post by skip mcshwang on 2008-06-03
Just load up synaptic and install the "smc" package.

---

### Post by hardingfele on 2008-06-04
thanks a lot! that worked as well :-D

---

