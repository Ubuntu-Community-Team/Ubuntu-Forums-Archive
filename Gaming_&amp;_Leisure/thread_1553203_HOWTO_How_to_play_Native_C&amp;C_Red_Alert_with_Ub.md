---
title: "HOWTO: How to play Native C&amp;C Red Alert with Ubuntu (+ bin file here compiled) !"
date: 2010-08-14
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2010-08-14
Hello,

So another game Native, so which means without Wine emulator. Native is great because games are not cycling your CPU for no reasons. They made an amazing work.

So here is the howto:

(1) So what is Red Alert 1 command and conqueer?
- [http://www.youtube.com/watch?v=E_Y6cVQUJb0](http://www.youtube.com/watch?v=E_Y6cVQUJb0)
- [http://www.youtube.com/watch?v=hKgTIkLMyZM&feature=related](http://www.youtube.com/watch?v=hKgTIkLMyZM&feature=related)

(2) First step
get the attached files, unpack them so that you get :
```
/home/username/openredalert/bin/data/mix 
```
where username is your username

and get this executable that I compiled for you (and me) : openredalert 

So get my four zip files, rename them as rar extension
- yes because I do not know how to split during packing with pkzip or file-roller, so I used rar :)
unrar x openredalert-light-split.part01.rar 
and it'll unpack those 4 split rar volumes

```
/bin$ md5sum openredalert 
1140e26c2e6989136ec3bde9efbedc1c  openredalert
```
(I attach the file)

(3) Download:
[ftp://ftp.games.skynet.be/spool1/games/ftp.westwood.com/redalert/previews/demo/ra95demo.zip](ftp://ftp.games.skynet.be/spool1/games/ftp.westwood.com/redalert/previews/demo/ra95demo.zip)

unzip this file and go into  ```
ra95demo/INSTALL$ ls
MAIN.MIX  RA95.EXE  RANOTES.ICO  README.WRI  REDALERT.INI  REDALERT.MIX  RESLIB.DLL  THIPX16.DLL  THIPX32.DLL
```

MAIN.MIX and REDALERT.mix into the folder of openredalert ie. :  under bin/data/mix

Copy the REDALERT.mix and MAIN.mix files from original archives of the game into the folder 'bin/data/mix' 

so that you have 
> 
| data/
|  |  |
|  |  | settings/ (many files don't touch !!!)
|  |  |
|  |  | mix/
|  |    |
|  |    | REDALERT.MIX
|  |    |
|  |    | MAIN.MIX
|  |
|  | openredalert (the executable copied)


(5) I have into bin/data/mix/
> 12687722 Aug 14 22:41 MAIN.MIX
11736696 Aug 14 22:41 REDALERT.MIX

(6) You need some libs 

```
sudo apt-get install libsdl-mixer1.2  
```

Me I have all those but you do not need all of them
ii  libsdl-image1.2                      1.2.10-2+b1                    image loading library for Simple DirectMedia
ii  libsdl-mixer1.2                      1.2.8-6+b1                     mixer library for Simple DirectMedia Layer 1
ii  libsdl-mixer1.2-dev                  1.2.8-6+b1                     development files for SDL1.2 mixer library
ii  libsdl1.2-dev                        1.2.14-6                       Simple DirectMedia Layer development files
ii  libsdl1.2debian                      1.2.14-6                       Simple DirectMedia Layer
ii  libsdl1.2debian-all                  1.2.14-6                       Simple DirectMedia Layer (with all available
rc  libsdl1.2debian-alsa                 1.2.14-6                       Simple DirectMedia Layer (with X11 and ALSA 

(7) go into bin where you have 10950427 Aug 14 21:44 openredalert

type ./openredalert


(8) 
Enjoy gaming !! You're welcome !

(9) Languages: Notice in case you would like something else than english:

Since I have the original game as cdrom, ie in french, I can use my own version. So from my genuine cdrom, I can still enjoy under linux the intro and videos; no need of wine nor windows. 

***Because LINUX is simply better! ***

--
References:
([URL]("http://www.ohloh.net/p/openredalert"))
here wiki [URL]("http://code.google.com/p/openredalert/wiki/HowTo")


Thank you to the developer !! Seem that openredalert will soon be dropped off, or I hoped not ... to relive !
[http://www.ohloh.net/p/openredalert/contributors/58742267719394](http://www.ohloh.net/p/openredalert/contributors/58742267719394)

---

### Post by Bonster on 2010-08-14
I just tryed this loL

It doesnt fully work but it was fast and the load times and everything, wish this project dont die, would love to see a native fully working Red Alert 1

---

### Post by frenchn00b on 2010-08-15
> **Bonster said:**
> I just tryed this loL

It doesnt fully work but it was fast and the load times and everything, wish this project dont die, would love to see a native fully working Red Alert 1

Could you play, fine? Otherwise, you need the genuine cdrom to have intros and bit more.

---

### Post by Bonster on 2010-08-15
Yea it plays OK but it was missing MCV and jerky movements

heres a video i made

[http://www.youtube.com/watch?v=_du4fDQeqZY](http://www.youtube.com/watch?v=_du4fDQeqZY)

---

### Post by frenchn00b on 2010-08-15
> **Bonster said:**
> Yea it plays OK but it was missing MCV and jerky movements

heres a video i made

[http://www.youtube.com/watch?v=_du4fDQeqZY](http://www.youtube.com/watch?v=_du4fDQeqZY)

wow it works 

nice video (and wallpaper, I prefer the one laying on the ground)

---

### Post by Geezusjedi on 2011-02-06
i have tried toi follow this guide and have helplessy gotten nowhere. i have the cd, i have extracted the files. i need a very indepth step by step guide with nothing left out. basicly i need to be told like a noobe how to do this to make sure i dont screw anything up. i am running ubuntu 10.04. dual core 3.0 amd cpu, 4 gigs of ram. 700 mb video ati video card.

---

