---
title: "New Racer Installer"
date: 2007-04-16
forum: Gaming &amp; Leisure
---

### Post by StarscreamD on 2007-04-16
I can install and run the new Racer install file from Loki's site. When I attempt to run the game, I can get to the car when this happens:
```
...
ODE Message 2: vector has zero size in dNormalize4()
Floating point exception (core dumped)
```

What's up with that? Can anyone else confirm this error?

---

### Post by RomeReactor on 2007-04-16
Hi. Is [this]("http://www.racer.nl/") the game you downloaded, or is it another one?

---

### Post by lotacus on 2007-04-16
your best bet would be to compile it yourself. It's pretty easy. You just download the source, un tar it, and run  ./configure then make then sudo make install. So now you have no excuse to say you are a n00b and don't know how to compile. :P I'm a n00b and i've learned in less then a day. It's fun fun fun! (linux and learning)

---

### Post by StarscreamD on 2007-04-16
To confirm, I downloaded the game listed at [http://www.racer.nl/](http://www.racer.nl/) However, I downloaded the installer from [http://liflg.org/](http://liflg.org/) I am attempting to compile my own version from source and see if that makes a difference. Can anyone else download the installer from Loki's site listed above and see if they can recreate this error?

---

### Post by StarscreamD on 2007-04-16
Well, I compiled version 0.5.0, and I must say I am impressed. I really want to get the updated version running. The Loki site has the updated installer for the latest beta version of racer, 0.5.3beta6 and I can get it to open the menus, but it will not get into the actual game. Anyone else having this problem or is it just me?

> ...
ODE Message 2: vector has zero size in dNormalize4()
Floating point exception (core dumped)

---

### Post by RomeReactor on 2007-04-16
Did you download the beta version? And if so, did you follow these instructions from the [Racer page]("http://www.racer.nl/dl_beta_linux.htm")?

> The latest Linux beta version is v0.5.3 beta 6. An installer has been made by Loki:
Download the Loki Racer version from [here]("http://www.liflg.org/?catid=6&gameid=13").
Run the downloaded file (racer_0.5.3beta6-english.run)

**Alternatively, follow these steps for a manual installation:**
Download the Windows Racer v0.5.3 beta 5 data files (18Mb/zip) from [here]("http://www.racer.nl/download/racer053b5.zip").
Download the Linux v0.5.3 beta 6 executable (and fmod v4.06) from [here]("http://www.racer.nl/download/linux/racer053b6test.zip") (19-3-07, 1Mb zip).
Unzip the Windows files; they'll probably end up in racer053b5/
Unzip the Linux zip and move the 'racer' and 'libfmodex.so' files into racer053b5/.
cd into racer053b5
Next, to run, first try:
export LD_LIBRARY_PATH=.:${LD_LIBRARY_PATH}; ./racer
If that doesn't work, try:
Copy libfmodex.so to /usr/local/lib (be careful not to overwrite any possible existing file) and run 'sudo ldconfig'.
 Run ./racer
Editing settings can be done using 'vi racer.ini', error checking after a run can be done with 'cat QLOG.txt'.

---

### Post by StarscreamD on 2007-04-16
Yes exactly. I can compile the source version, and I can get the older version of the beta up. This new installer, however, creates that error.

---

### Post by RomeReactor on 2007-04-16
I'm downloading the beta installer from loki (racer_0.5.3beta6-english.run); I'll post back if I make any progress.

---

### Post by RomeReactor on 2007-04-16
I couldn't find the error; I just ran the installer and it installed correctly here, without any other input from me; did you try to install it using **sudo**?

```
sudo sh racer_0.5.3beta6-english.run
```

perhaps the problem has to do with not having hardware acceleration enabled for your graphics card. Also, is it ATI or NVIDIA?

---

### Post by StarscreamD on 2007-04-17
nVidia GeForce MX 420 card. I did not use sudo. It must be something on my end.. what could it be? I have no other problems and I have multiple other games... btw RomeReactor thanks for your help thus far.

---

### Post by RomeReactor on 2007-04-17
It appears this is [a known bug]("http://forum.rscnet.org/showthread.php?t=70919&page=3") related to the [Open Dynamics Engine]("http://en.wikipedia.org/wiki/Open_Dynamics_Engine"). Does the stable version (0.5.0) have the same problem on your system? Can you try installing the game on another computer with a different video card?

---

### Post by StarscreamD on 2007-04-17
Both the stable version and the old beta run fine. I guess I'll just have to settle for those. I don't have another box to test on. Thanks again.

---

### Post by fakie_flip on 2007-04-17
The game won't install for me either :( The gui loki installer came up. I clicked start install and everything appeared to go okay. When I ran the game from gnome-terminal, these are the errors I got. Also the screen goes black and the mouse pointer turns red for a split second while the game tries to start. I am using Feisty.

```
chris@ubuntu:~/Desktop$ sudo ./racer_0.5.3beta6-english.run 
Password:
Verifying archive integrity... All good.
Uncompressing Racer 0.5.3beta6-english Installer.............................
chris@ubuntu:~/Desktop$ racer 
--- application start ---
** [racer/23848] Can't open log file (QLOG)
QApp: new QDisplay
Racer version: 0.5.3 beta 6 (Mar 19 2007/21:40:23)
** [racer/23848] Can't open log file (QLOG)
RMultiview:Create()
Multiview: we are the master/server
### Q Memory Report - no allocations ###
### Q Memory Report - no allocations ###
QImage::Read("data/fonts/din14.tga")
QLicensePool (RMGR:Create):
QImage::Read("data/images/skidmark.tga")
QImage::Read("data/images/smap_whitesun_add.tga")
QImage::Read("data/images/track_lt.tga")
QImage::Read("data/images/track_rt.tga")
QImage::Read("data/images/track_up.tga")
QImage::Read("data/images/track_dn.tga")
QImage::Read("data/images/track_fw.tga")
QImage::Read("data/images/track_bw.tga")
QImage::Read("data/images/sun_lt.tga")
QImage::Read("data/images/sun_rt.tga")
QImage::Read("data/images/sun_up.tga")
QImage::Read("data/images/sun_dn.tga")
QImage::Read("data/images/sun_fw.tga")
QImage::Read("data/images/sun_bw.tga")
RAutoJoin:Create()
Autojoin: we are the master/server
QImage::Read("data/images/repbuts.tga")
Can't init FMOD
** [racer/23848] Can't open log file (QLOG)
chris@ubuntu:~/Desktop$ 
```

I also tried this.

```
chris@ubuntu:/usr/local/games/racer/lib$ sudo cp -iv libfmodex.so /usr/local/lib/
`libfmodex.so' -> `/usr/local/lib/libfmodex.so'
chris@ubuntu:/usr/local/games/racer/lib$ export LD_LIBRARY_PATH=.:${LD_LIBRARY_PATH}
chris@ubuntu:/usr/local/games/racer/lib$

```

I got that from the directions for installing the beta. Nothing worked.

---

### Post by RomeReactor on 2007-04-17
> **fakie_flip said:**
> Can't init FMOD

Hi. Did you try copying **libfmodex.so** to "/lib" as explained in the troubleshooting section of the [installation guide]("http://www.racer.nl/dl_beta_linux.htm")? Also in [this thread]("http://ubuntuforums.org/showthread.php?t=119085") is suggested using another version of libfmod (though the thread is a year old).

---

### Post by fakie_flip on 2007-04-22
I just tried the beta. It showed only in a small portion of the top left of my screen. I clicked on free race. It loaded and then crashed. Here are the errors I got while running it in gnome-terminal. I want to get this game working. The screenshots look very nice.

```
chris@ubuntu:~/MY GAMES$ racer 
--- application start ---
** [racer/23065] Can't open log file (QLOG)
QApp: new QDisplay
Racer version: 0.5.3 beta 6 (Mar 19 2007/21:40:23)
** [racer/23065] Can't open log file (QLOG)
RMultiview:Create()
Multiview: we are the master/server
### Q Memory Report - no allocations ###
### Q Memory Report - no allocations ###
QImage::Read("data/fonts/din14.tga")
QLicensePool (RMGR:Create):
QImage::Read("data/images/skidmark.tga")
QImage::Read("data/images/smap_whitesun_add.tga")
QImage::Read("data/images/track_lt.tga")
QImage::Read("data/images/track_rt.tga")
QImage::Read("data/images/track_up.tga")
QImage::Read("data/images/track_dn.tga")
QImage::Read("data/images/track_fw.tga")
QImage::Read("data/images/track_bw.tga")
QImage::Read("data/images/sun_lt.tga")
QImage::Read("data/images/sun_rt.tga")
QImage::Read("data/images/sun_up.tga")
QImage::Read("data/images/sun_dn.tga")
QImage::Read("data/images/sun_fw.tga")
QImage::Read("data/images/sun_bw.tga")
RAutoJoin:Create()
Autojoin: we are the master/server
QImage::Read("data/images/repbuts.tga")
QSample::Load(data/audio/road.wav)
QSample::Load(data/audio/grass.wav)
QSample::Load(data/audio/gravel.wav)
QSample::Load(data/audio/kerb.wav)
QSample::Load(data/audio/sand.wav)
QImage::Read("data/images/race.tga")
QImage::Read("data/images/standings.tga")
QSample::Load(data/audio/horn_lo.wav)
QSample::Load(data/audio/horn_hi.wav)
QSample::Load(data/audio/heli_inside.wav)
QImage::Read("data/images/car_indicator.tga")
QImage::Read("data/fonts/din14.tga")
QImage::Read("data/images/wheel.tga")
QImage::Read("data/images/menu_bgr.jpg")
QImage::Read("data/images/logo.tga")
QImage::Read("data/fonts/din14.tga")
QImage::Read("data/fonts/realvirtue40.tga")
Autojoin server - poll
Autojoin server - poll
Autojoin server - poll
Autojoin server - poll
Autojoin server - poll
Autojoin server - poll
QInfo:Write(); file (racer.ini) can't be written
** [racer/23065] Can't open log file (QLOG)
QInfo:Write(); file (racer.ini) can't be written
** [racer/23065] Can't open log file (QLOG)
RMenuDestroy()
RMenu Destroy(); count=10
RMenuDestroy()
QImage::Read("data/images/loading.jpg")
RTrackVRML:Load()
QImage::Read("data/images/pacenotes/l1.tga")
QImage::Read("data/images/pacenotes/l2.tga")
QImage::Read("data/images/pacenotes/l3.tga")
QImage::Read("data/images/pacenotes/l4.tga")
QImage::Read("data/images/pacenotes/l5.tga")
QImage::Read("data/images/pacenotes/r1.tga")
QImage::Read("data/images/pacenotes/r2.tga")
QImage::Read("data/images/pacenotes/r3.tga")
QImage::Read("data/images/pacenotes/r4.tga")
QImage::Read("data/images/pacenotes/r5.tga")
QImage::Read("data/images/pacenotes/start.tga")
QImage::Read("data/images/pacenotes/finish.tga")
QImage::Read("data/tracks/carlswood_nt/sun_lt.tga")
QImage::Read("data/tracks/carlswood_nt/sun_rt.tga")
QImage::Read("data/tracks/carlswood_nt/sun_up.tga")
QImage::Read("data/tracks/carlswood_nt/sun_dn.tga")
QImage::Read("data/tracks/carlswood_nt/sun_fw.tga")
QImage::Read("data/tracks/carlswood_nt/sun_bw.tga")
QImage::Read("data/images/flare0.bmp")
QImage::Read("data/images/flare1.bmp")
QImage::Read("data/images/flare2.bmp")
QImage::Read("data/images/flare3.bmp")
QImage::Read("data/images/flare4.bmp")
QImage::Read("data/models/conea.bmp")
QImage::Read("data/tracks/carlswood_nt/road.tga")
QImage::Read("data/tracks/carlswood_nt/sky.tga")
QImage::Read("data/tracks/carlswood_nt/road_start.tga")
QImage::Read("data/tracks/carlswood_nt/kerbs.tga")
QImage::Read("data/tracks/carlswood_nt/concrete02.tga")
QImage::Read("data/tracks/carlswood_nt/gravel.tga")
QImage::Read("data/tracks/carlswood_nt/grass1a.tga")
QImage::Read("data/tracks/carlswood_nt/sand.tga")
QImage::Read("data/tracks/carlswood_nt/xs01.tga")
QImage::Read("data/tracks/carlswood_nt/xs02.tga")
QImage::Read("data/tracks/carlswood_nt/tree1.tga")
QImage::Read("data/tracks/carlswood_nt/tree3.tga")
QImage::Read("data/tracks/carlswood_nt/tretp.tga")
QImage::Read("data/tracks/carlswood_nt/tretopf.tga")
QImage::Read("data/tracks/carlswood_nt/woods01.tga")
QImage::Read("data/tracks/carlswood_nt/twalltp.tga")
QImage::Read("data/tracks/carlswood_nt/twall.tga")
QImage::Read("data/tracks/carlswood_nt/signs.tga")
QImage::Read("data/tracks/carlswood_nt/road_tracks01.tga")
QImage::Read("data/tracks/carlswood_nt/fence02.tga")
QImage::Read("data/tracks/carlswood_nt/iron_fence.tga")
QImage::Read("data/tracks/carlswood_nt/met_galv.tga")
QImage::Read("data/tracks/carlswood_nt/rock.tga")
QImage::Read("data/tracks/carlswood_nt/s_start.tga")
QImage::Read("data/tracks/carlswood_nt/s_201m.tga")
QImage::Read("data/tracks/carlswood_nt/s_402m.tga")
QImage::Read("data/tracks/carlswood_nt/s_1000m.tga")
QImage::Read("data/tracks/carlswood_nt/c_orange.tga")
QImage::Read("data/tracks/carlswood_nt/c_white.tga")
QImage::Read("data/tracks/carlswood_nt/wood_old.tga")
RNetwork:ConnectToServer()
QImage::Read("data/images/loading.jpg")
QImage::Read("data/fonts/realvirtue40.tga")
RNetwork: waiting for connecting id response...
RNetwork: out of loop, client connected: 1, id 70
RNetwork: succesfully connected to server.
QImage::Read("data/images/loading.jpg")
QInfo:Write(); file (data/tracks/carlswood_nt/ai/lambomurcielago.ini) can't be written
** [racer/23065] Can't open log file (QLOG)
QImage::Read("data/cars/lambomurcielago/fresnel.tga")
QImage::Read("data/cars/lambomurcielago/lambobody.tga")
QImage::Read("data/cars/lambomurcielago/glass.tga")
QImage::Read("data/cars/lambomurcielago/underbodytex.tga")
QImage::Read("data/cars/lambomurcielago/interior.tga")
QImage::Read("data/cars/lambomurcielago/tirerim.tga")
QImage::Read("data/cars/lambomurcielago/tirerimrear.tga")
QImage::Read("data/cars/lambomurcielago/tireriminside.tga")
QImage::Read("data/cars/lambomurcielago/brakedisktext.tga")
QImage::Read("data/cars/lambomurcielago/tiretread.tga")
QImage::Read("data/cars/lambomurcielago/shadowmap.tga")
QImage::Read("data/cars/lambomurcielago/brakelight.tga")
QImage::Read("data/cars/lambomurcielago/shadow.tga")
QImage::Read("data/images/smoke.tga")
DTextureObject ctor (data/images/smoke.tga)QImage::Read("data/images/gravel_dirt.tga")
DTextureObject ctor (data/images/gravel_dirt.tga)QImage::Read("data/images/gravel_smoke.tga")
DTextureObject ctor (data/images/gravel_smoke.tga)car.ini of 'lambomurcielago' has body.restitution_coeff defined, which is obsolete. Use racer.ini's collision.restitution instead
** [racer/23065] Can't open log file (QLOG)
QSample::Load(data/cars/lambomurcielago/2000.wav)
QSample::Load(data/cars/lambomurcielago/3000.wav)
QSample::Load(data/cars/lambomurcielago/3600.wav)
QSample::Load(data/cars/lambomurcielago/5000.wav)
QSample::Load(data/cars/lambomurcielago/6000.wav)
QSample::Load(data/cars/lambomurcielago/7000.wav)
QSample::Load(data/cars/lambomurcielago/8000.wav)
QSample::Load(data/cars/lambomurcielago/wind1.wav)
QSample::Load(data/cars/lambomurcielago/wind2.wav)
QSample::Load(data/cars/lambomurcielago/wind3.wav)
QSample::Load(data/cars/lambomurcielago/skid.wav)
QSample::Load(data/audio/horn.wav)
QSample::Load(data/audio/shift_miss.wav)
QSample::Load(data/cars/lambomurcielago/starter.wav)
QImage::Read("data/cars/lambomurcielago/kmh.tga")
QImage::Read("data/cars/lambomurcielago/needle.tga")
QImage::Read("data/cars/lambomurcielago/rpm.tga")
QImage::Read("data/cars/lambomurcielago/needle.tga")
QImage::Read("data/cars/lambomurcielago/digitalfont.tga")
QImage::Read("data/cars/lambomurcielago/digitalfont.tga")
QImage::Read("data/cars/lambomurcielago/times.tga")

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()

ODE Message 2: vector has zero size in dNormalize4()
Floating point exception
chris@ubuntu:~/MY GAMES$
```

---

### Post by fakie_flip on 2007-04-22
> **RomeReactor said:**
> Hi. Did you try copying **libfmodex.so** to "/lib" as explained in the troubleshooting section of the [installation guide]("http://www.racer.nl/dl_beta_linux.htm")? Also in [this thread]("http://ubuntuforums.org/showthread.php?t=119085") is suggested using another version of libfmod (though the thread is a year old).

Yes, I did. I showed you this in my first post.

```
chris@ubuntu:/usr/local/games/racer/lib$ sudo cp -iv libfmodex.so /usr/local/lib/
`libfmodex.so' -> `/usr/local/lib/libfmodex.so'
chris@ubuntu:/usr/local/games/racer/lib$ sudo ldconfig 
chris@ubuntu:/usr/local/games/racer/lib$ 
```

---

### Post by RomeReactor on 2007-04-22
Well, you copied it to **/usr/local/lib**; however, in the guide there's a [troubleshooting section]("http://www.racer.nl/dl_beta_linux.htm") at the bottom:

> libfmodex.so is not found; copy libfmodex.so as root to /lib

Also, did you run **sudo ldconfig** after you copied libfmodex.so to /usr/local/lib?

---

### Post by srinivaschavan on 2007-05-07
While trying to run racer on feisty fawn amd64, I was also seeing the FMOD init failed message. Seems like my rhythmbox running in the background was the culprit. After quitting rhythmbox, racer started up fine. So, please try stopping any applications that might be using sound and see if racer works.

---

### Post by fakie_flip on 2007-05-07
This game seems buggy. Yes, I am doing everything you said that are from the instructions. Just look at the commands I am using.

chris@ubuntu:~$ cd /usr/local/games/racer/lib/
chris@ubuntu:/usr/local/games/racer/lib$ sudo cp -vi libfmodex.so /lib/
Password:
`libfmodex.so' -> `/lib/libfmodex.so'
chris@ubuntu:/usr/local/games/racer/lib$ sudo ldconfig 
chris@ubuntu:/usr/local/games/racer/lib$ racer 
--- application start ---
** [racer/25339] Can't open log file (QLOG)
QApp: new QDisplay
Racer version: 0.5.3 beta 6 (Mar 19 2007/21:40:23)
** [racer/25339] Can't open log file (QLOG)
RMultiview:Create()
Multiview: we are the master/server
### Q Memory Report - no allocations ###
### Q Memory Report - no allocations ###
QImage::Read("data/fonts/din14.tga")
QLicensePool (RMGR:Create):
QImage::Read("data/images/skidmark.tga")
QImage::Read("data/images/smap_whitesun_add.tga")
QImage::Read("data/images/track_lt.tga")
QImage::Read("data/images/track_rt.tga")
QImage::Read("data/images/track_up.tga")
QImage::Read("data/images/track_dn.tga")
QImage::Read("data/images/track_fw.tga")
QImage::Read("data/images/track_bw.tga")
QImage::Read("data/images/sun_lt.tga")
QImage::Read("data/images/sun_rt.tga")
QImage::Read("data/images/sun_up.tga")
QImage::Read("data/images/sun_dn.tga")
QImage::Read("data/images/sun_fw.tga")
QImage::Read("data/images/sun_bw.tga")
RAutoJoin:Create()
Autojoin: we are the master/server
QImage::Read("data/images/repbuts.tga")
Can't init FMOD
** [racer/25339] Can't open log file (QLOG)
chris@ubuntu:/usr/local/games/racer/lib$

---

### Post by Gen2ly on 2007-05-17
Installed using the Loki Installer.  "Free Driving: works great.  All the other buttons, will seg fault:
```
racer: line 123: 12114 Segmentation fault      ./${GAME_BINARY} ${CMD_ARGS} "$@"
```

"Free Driving" was fun.

weeeeeeeeeeeeeeeee

graphics are freakin awesome!

---

### Post by fakie_flip on 2007-05-17
> **Dirk.R.Gently said:**
> Installed using the Loki Installer.  "Free Driving: works great.  All the other buttons, will seg fault:
```
racer: line 123: 12114 Segmentation fault      ./${GAME_BINARY} ${CMD_ARGS} "$@"
```

"Free Driving" was fun.

weeeeeeeeeeeeeeeee

graphics are freakin awesome!

What was the name of the file you installed from? If it is different than the one I have, I will try yours.

---

### Post by Gen2ly on 2007-05-17
> **fakie_flip said:**
> What was the name of the file you installed from? If it is different than the one I have, I will try yours.

I used the beta6 on this [page]("http://www.liflg.org/?catid=6&gameid=13").  This will be something to watch over the next year.

---

### Post by Eriksmits596 on 2007-09-10
Hmm.. I've installed the beta version of racer(loki's installer) and it worked fine with the installation, but when I have started the game, it just disappears after about 5 seconds... what should I do?

---

