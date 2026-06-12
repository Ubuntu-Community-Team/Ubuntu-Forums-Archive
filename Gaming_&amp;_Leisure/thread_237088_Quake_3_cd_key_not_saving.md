---
title: "Quake 3 cd key not saving"
date: 2006-08-15
forum: Gaming &amp; Leisure
---

### Post by shanet on 2006-08-15
Hi, I seem to have the same problem as this gentleman here, [in this thread](http://www.ubuntuforums.org/showthread.php?t=37877&highlight=quake+cd+key). Basically I keep having to re-enter my cd key every time I start quake3. Also bringing up the console shows me the error... I see cannot q write baseq3, cannot write q3config.cfg.

I suppose this might be because I ran the installer as sudo, but that was the only way it would work. Does anyone have an idea what permissions I should change to make q3config writable? Deleting it doesn't work, chmoding it to everything under the sun doesn't work... and chowning it doesn't work either... plus doesn't it keep my cdkey in a different file? Help greatly appreciated.

---

### Post by william_nbg on 2006-08-15
Have you tried changing the permissions on the config file were the key is stored??

Just change it to something writeable, or even 777 if its for just a game.

sudo Chmod 777 (filename)

---

### Post by HAARP on 2006-08-15
sudo chown -hR shanet:shanet /home/shanet/.quake3

---

### Post by shanet on 2006-08-15
thanks for your ideas guys

william_nbg; I've tried that alright, but even at 777 I am still told > 
Couldn't write q3config.cfg.
Couldn't write q3config.cfg.
Couldn't write baseq3.

I even 777'd the whole baseq3 directory and it didn't work ](*,) I later tried deleting the q3config.cfg file, then did touch q3config.cfg and changed its permissions... still no joy

HAARP: the .quake3 in my home directory doesn't exist;
> 
chown: ní féidir `/home/shanet/.quake3' a rochtain: No such file or directory

so I created one and did the command you gave me, but still received the same error. to be sure to be sure I checked whether there was a .quake3 in /root but there wasn't.

---

### Post by shanet on 2006-08-15
here is the contents of my quake3 directory

> shanet@generalmiaow:/usr/local/games/quake3$ ls -l
iomlán 2604
drwxr-xr-x 2 shanet shanet    4096 2006-08-15 21:37 baseq3
-rw-r--r-- 1 root   root      6505 2006-08-15 21:06 CHANGES-1.32.txt
drwxr-xr-x 4 root   root      4096 2006-08-15 21:06 Docs
-rw-r--r-- 1 root   root      2217 2006-08-15 21:06 INSTALL
drwxr-xr-x 2 root   root      4096 2006-08-15 21:06 missionpack
drwxr-xr-x 3 root   root      4096 2006-08-15 21:06 pb
-rw-r--r-- 1 root   root      9949 2006-08-15 21:06 Q3A_EULA.txt
-rwxr-xr-x 1 root   root       131 2006-08-15 21:06 quake3
-rwxr-xr-x 1 root   root       134 2006-08-15 21:06 quake3-smp
-rwxr-xr-x 1 root   root   1285436 2006-08-15 21:06 quake3-smp.x86
-rwxr-xr-x 1 root   root   1284028 2006-08-15 21:06 quake3.x86
-rw-r--r-- 1 root   root      4276 2006-08-15 21:06 quake3.xpm
-rw-r--r-- 1 root   root     15619 2006-08-15 21:06 README-Id-7-26-01.html
-rw-r--r-- 1 root   root     11950 2006-08-15 21:06 README-linux.txt
shanet@generalmiaow:/usr/local/games/quake3$

and my baseq3 directory

> shanet@generalmiaow:/usr/local/games/quake3/baseq3$ ls -l
iomlán 493900
-r-xr-xr-x 1 root   root          49 2006-08-15 21:09 blank.htm
-r-xr-xr-x 1 root   root   479493658 2006-08-15 21:12 pak0.pk3
-rw-r--r-- 1 root   root       10782 2006-08-15 21:12 pak1.pk3
-rw-r--r-- 1 root   root     7511182 2006-08-15 21:06 pak2.pk3
-rw-r--r-- 1 root   root      276305 2006-08-15 21:06 pak3.pk3
-rw-r--r-- 1 root   root     9600350 2006-08-15 21:06 pak4.pk3
-rw-r--r-- 1 root   root      191872 2006-08-15 21:06 pak5.pk3
-rw-r--r-- 1 root   root     7346884 2006-08-15 21:06 pak6.pk3
-rw-r--r-- 1 root   root      320873 2006-08-15 21:06 pak7.pk3
-rw-r--r-- 1 root   root      454478 2006-08-15 21:06 pak8.pk3
-rw-r--r-- 1 shanet shanet         0 2006-08-15 21:37 q3config.cfg
shanet@generalmiaow:/usr/local/games/quake3/baseq3$


also, I'm not sure where the key is stored. :-k I don't think it's the q3config.cfg file.

---

### Post by shanet on 2006-08-15
ahhhh it works now. turns out the local config for q3 was in ~/.q3a not ~/.quake3 :) SOLVED! using HAARP's advice. thanks to both of you

---

