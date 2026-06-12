---
title: "Unable to play Supertuxkart"
date: 2012-03-10
forum: Gaming &amp; Leisure
---

### Post by mastablasta on 2012-03-10
I don't know what is wrong. I installed it from playdeb. it runs ok, let's me select the track, but when i want to play it crashes. upon running it from terminal i get this:

```
supertuxkart
Irrlicht Engine version 1.8.0-alpha
Linux 2.6.35-32-generic #66-Ubuntu SMP Mon Feb 13 21:04:12 UTC 2012 i686
Could not load sprite bank because the file does not exist: #DefaultFont
[FileManager] Data files will be fetched from: '/usr/share/games/supertuxkart/'
Env var LANG = 'en_US.UTF-8'
Adding language fallback en
[IrrDriver] Creating NULL device
Irrlicht Engine version 1.8.0-alpha
Linux 2.6.35-32-generic #66-Ubuntu SMP Mon Feb 13 21:04:12 UTC 2012 i686
Could not load sprite bank because the file does not exist: #DefaultFont
[IrrDriver] Trying OpenGL rendering.
[IrrDriver] Trying to create device with 32 bits
[IrrDriver Temp Logger] Level 3: Could not load sprite bank because the file does not exist: #DefaultFont
WARNING: DeviceConfig::deserializeAction : action 'pauserace' is unknown
Ignoring an ill-formed keyboard action in input config.
startMusic : m_normal_filename=</usr/share/games/supertuxkart//data//music/MayDayMayhem.ogg>, gain=0.7
WARNING: Music not playing when it should be. Source state: 4116
[Irrlicht Error] FBO has one or several incomplete image attachments
[Irrlicht Error] FBO error
supertuxkart: COpenGLTexture.cpp:888: bool irr::video::checkFBOStatus(irr::video::COpenGLDriver*): Assertion `!(true)' failed.
Aborted

```

it says i have:

```
01:00.0 VGA compatible controller: ATI Technologies Inc M10 NQ [Radeon Mobility 9600]

display:0
                description: VGA compatible controller
                product: M10 NQ [Radeon Mobility 9600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:16 memory:b0000000-bfffffff ioport:e000(size=256) memory:feae0000-feaeffff memory:feac0000-feadffff

```


but actually it is a Radeon 9600 XT or it could be that it's a 9800XT i forgot...using opensource drivers...

CPU is dualcore Intel(R) Celeron(R) CPU        E3300  @ 2.50GHz
1.3GB ram
Kubuntu 10.10

---

### Post by ajgreeny on 2012-03-10
What version of supertuxkart is it?

I have version 0.7 which just about runs on my old system with a Sempron 2400+ and 2GB ram, with an ATI 9200SE card, also running the open source driver.
I also tried the updated version of STK 0.7.x (I can't remember exactly the version from playdeb) and that also crashed every time I tried to play at about the same point as you describe.

---

### Post by Johnny3 on 2012-03-10
Have you tried uninstalling that one and installing the one in Software Center?
Good Luck and God Bless Johnny3 65+++

---

### Post by mastablasta on 2012-03-10
version is 0.7.1b-1

i did try the one from "software center" (which was tuxkart and it worked perfectly), however upon adding the playdeb repos it automaticly upgraded to supertuxkart. supertuxkart has more options, new tracks, improved graphics and more game modes. So i would like to try it out.

---

### Post by ajgreeny on 2012-03-10
Yes, I think that is the version that I could not get to run as well.

---

### Post by Arthur_D on 2012-03-10
mastablasta, your drivers/videocard seems to have trouble with framebuffer objects. I suggest going to the in-game options and turn it off (there's a checkbox). You may get some graphical glitches, but at least it shouldn't crash. Otherwise, try other drivers.

---

### Post by mastablasta on 2012-03-11
> **Arthur_D said:**
> mastablasta, your drivers/videocard seems to have trouble with framebuffer objects. I suggest going to the in-game options and turn it off (there's a checkbox). You may get some graphical glitches, but at least it shouldn't crash. Otherwise, try other drivers.


thatnks i will try that. also other drivers when the LTS comes out :-)
for now supertuxkart is the only one giviing me such a hard time. Urban terror, Sauerbraten and similar 3D work normaly.

---

### Post by mastablasta on 2012-03-11
well there is no such option in the options screen. only to reduce graphics animaitons and change sacreen resolution. or fullscreen-windowed mode. :-(

---

### Post by whatthefunk on 2012-03-11
supertuxkart is in the repos.  Try installing from a terminal:

```
sudo apt-get install supertuxkart
```

I just installed it on my machine to try it out and it works perfectly.

---

### Post by mastablasta on 2012-03-11
good for you. note that i am using 10.10 which i think doesn't have supertuxkart but tuxkart by default tuxkart works, however supertuxcart gotten via PPA form play deb crashes to desktop when loading the track.

---

### Post by Arthur_D on 2012-03-11
> **mastablasta said:**
> well there is no such option in the options screen. only to reduce graphics animaitons and change sacreen resolution. or fullscreen-windowed mode. :-(
Try the latest static binary from the website at [http://supertuxkart.net/Downloads#Linux](http://supertuxkart.net/Downloads#Linux). The PPA is a couple versions behind if it's version 0.7.1. The latest version of the game is 0.7.3.

---

### Post by madjr on 2012-03-11
> **mastablasta said:**
> good for you. note that i am using 10.10 which i think doesn't have supertuxkart but tuxkart by default tuxkart works, however supertuxcart gotten via PPA form play deb crashes to desktop when loading the track.

why not start testing kubuntu 12.04, drivers imo work better too :)

---

### Post by mastablasta on 2012-03-12
> **Arthur_D said:**
> Try the latest static binary from the website at [http://supertuxkart.net/Downloads#Linux](http://supertuxkart.net/Downloads#Linux). The PPA is a couple versions behind if it's version 0.7.1. The latest version of the game is 0.7.3.
 
i will give it a try when i get another session on that mashcine.
 
> **madjr said:**
> why not start testing kubuntu 12.04, drivers imo work better too :)
 
It's a production mashcine from my wife. i fear that if i went beta bug will increase and since i have no time to fix them (i.e. find a fix) during the week she would be left with a brick.
 
also i plan to upgrade, which reminds me that i need to open a thread about it since i dont' know which PPA's i need to disable. I am using PPA for a newer KDE than default and also quite a lot of newer programme versions. i needed the new versions to be compatible with the widnows mashcine. Linux realyl should make it easier to upgrade programmes only...

---

### Post by ajgreeny on 2012-03-12
I have just tried the STK 0.7.3 from the link in Arthur_D's post, and it runs extremely well even on my old machine running 10.04.

Well worth trying!!

Just download the archive, extract it somewhere in your home and run the run_game.sh file with a double click.

---

### Post by mastablasta on 2012-03-17
Using the linked binary solved the problem. Extract, double click it and play.

PPA's should update to this version.

---

