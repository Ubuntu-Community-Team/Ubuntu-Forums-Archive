---
title: "Help with Unity and games"
date: 2012-09-22
forum: Gaming &amp; Leisure
---

### Post by Horadranin on 2012-09-22
Hi, I'm playing Rochard (from Humble Bundle 6) in Ubuntu 12.04 (Precise Pangolin) with latest upgrades and I'm getting some screen trashes sometimes and whenever a click middle mouse button.  It is a bit annoying but never prevent me to continue playing.
But recently I reached the point I get the grenade launcher and every time I shoot the screen trashes and when it back to normal my the character turns himself to left and don't shoot. Now it is preventing me to go further.

Also, I think it's not a game bug but a Unity (the DE not the game's engine ) one since I booted my (good and) old Ubuntu 10.10, installed Rochard, copied the save game, and played WITHOUT ANY disturbance!

By the way, Torchlight outputs no sound in 12.04 and is fine in 10.10. 

Is there any workaround (besides play in Maverick Meerkat) for these bugs? It's quite disappointing see a new and LTS  release be a lot more buggy than an old and dead one.

My hardware:
Intel Core i7 860
4 GB RAM
AMD/ATI Radeon HD 5870 and proprietary drivers

---

### Post by jadus on 2012-09-24
I have same problem. I have HB6 and i downloanded Rochard, because i like it. In game i have many lags and low FPS (20 max). 

I have i5 2,4Ghz
8GB DDR3 RAM
AMD Radeon HD 6650M (proprietory drivers)

Some help?

---

### Post by zombifier25 on 2012-09-24
Compiz does not work well with games. In order to play games smoothly, you need to install a lightweight DE (like LXDE, or better yet, just Openbox), and play games in there.

---

### Post by Horadranin on 2012-09-24
> **zombifier25 said:**
> Compiz does not work well with games. In order to play games smoothly, you need to install a lightweight DE (like LXDE, or better yet, just Openbox), and play games in there.

Actually, I just switched my session to Ubuntu 2D and everething went fine with Rochard. Torchlight still output no sound in 12.04.

In 12.10 Canonical will kill Ubuntu 2D session. It will be a desaster since Unity really sucks for games :(

Anyway, anything to help me with Torchlight?

---

### Post by outolintu on 2012-09-24
Hi.
I have problems with some of my games like Torchlight, Rochard, Limbo and few others. They install okay, but none of them launch, when I try to open one of them nothing happens.

I'm good with computers, but I'm pretty new with Ubuntu and I'm lost. :)

Terminal told me this when trying to launch Torchlight:

owner@owner-laptop:~$ /usr/local/games/Torchlight/Torchlight.bin.x86
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  42
  Current serial number in output stream:  42

And this with Rochard:

owner@owner-laptop:~$ /opt/rochard/Rochard.app
Found path: /opt/rochard/Rochard.app
Mono path[0] = '/opt/rochard/Rochard_Data/Managed'
Mono path[1] = '/opt/rochard/Rochard_Data/Mono'
Aborted (core dumped)

Any ideas?

---

### Post by jadus on 2012-09-25
> **zombifier25 said:**
> Compiz does not work well with games. In order to play games smoothly, you need to install a lightweight DE (like LXDE, or better yet, just Openbox), and play games in there.

Could it work with MATE desktop without Compiz?

---

### Post by zombifier25 on 2012-09-25
> **outolintu said:**
> Hi.
I have problems with some of my games like Torchlight, Rochard, Limbo and few others. They install okay, but none of them launch, when I try to open one of them nothing happens.

I'm good with computers, but I'm pretty new with Ubuntu and I'm lost. :)

Terminal told me this when trying to launch Torchlight:

owner@owner-laptop:~$ /usr/local/games/Torchlight/Torchlight.bin.x86
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  42
  Current serial number in output stream:  42

And this with Rochard:

owner@owner-laptop:~$ /opt/rochard/Rochard.app
Found path: /opt/rochard/Rochard.app
Mono path[0] = '/opt/rochard/Rochard_Data/Managed'
Mono path[1] = '/opt/rochard/Rochard_Data/Mono'
Aborted (core dumped)

Any ideas?

Post your system specs (RAM, Video card, etc.). Also, try contacting the developers of the games. They will have a better idea of what happened.

> **jadus said:**
> Could it work with MATE desktop without Compiz?

Probably. I haven't tried MATE yet, but I can see no reason why it shouldn't,

---

### Post by vexorian on 2012-09-25
My advice about running full screen games in unity (actually, it is compiz' fault, not unity's) is [don't](http://vexfloss.blogspot.com/2012/09/why-and-how-i-use-single-terminal.html)

---

### Post by jadus on 2012-09-25
Now i am running with new Cinnamon 1.6 and it's much much better... but it's still a bit laggy. But now it's playable. I think it's because AMD doesn't care about linux as good as windows.

---

### Post by outolintu on 2012-09-25
> **outolintu said:**
> Hi.
I have problems with some of my games like Torchlight, Rochard, Limbo and few others. They install okay, but none of them launch, when I try to open one of them nothing happens.

I'm good with computers, but I'm pretty new with Ubuntu and I'm lost. :)

Terminal told me this when trying to launch Torchlight:

owner@owner-laptop:~$ /usr/local/games/Torchlight/Torchlight.bin.x86
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  42
  Current serial number in output stream:  42

And this with Rochard:

owner@owner-laptop:~$ /opt/rochard/Rochard.app
Found path: /opt/rochard/Rochard.app
Mono path[0] = '/opt/rochard/Rochard_Data/Managed'
Mono path[1] = '/opt/rochard/Rochard_Data/Mono'
Aborted (core dumped)

Any ideas?

My computers specs are:

Intel Core i5 450M / 2.4 GHz
ATI Mobility Radeon HD 5650
RAM 4 Gb

---

### Post by MutantJohn on 2012-09-25
I don't know how relevant this is or not but I heard that Unity has the lowest OpenGL performance benchmarks.

So I switched from Unity to Gnome 3 (I'm on 12.04 too)and not only was I finally able to alt-tab out of Heroes of Newerth but I did notice that game was running at a much more stable FPS. Plus, I'm kind of grooving on the design of it now.

---

### Post by jadus on 2012-09-26
Torchlight, BIT.TRIP runner are good... Lowest FPS in torchlight 25 and in runner 30... So i think it's about Unity game engine (not that Unity) because in Rochard my processor runs only on 800Mhz, but during Torchlight or runner it's about 2,4Ghz

---

### Post by jadus on 2012-09-26
it's a bit paradox, but when i install muffin (sudo apt-get muffin, probably cinnamon's ppa is required) and it enabled some effects and fps increased... Wonderful :D but i afraid we must wait for next version of amd video drivers and hope in tear free option i amdcccle

---

### Post by oldos2er on 2012-09-26
Moved to Gaming & Leisure.

---

### Post by outolintu on 2012-09-26
I tried totally re-installing whole Ubuntu 12.04 and downloading all the nessessary updates and additional drivers, still nothing.

Really starting to wonder what is my Ubuntu missing?

---

### Post by oldrocker99 on 2012-09-26
Hmmm...I have the Unity DE on my machine, but I use MATE almost exclusively and have no problems. I'm using Ultimate Edition 3.4, installed MATE from the PPA, and am keeping Metacity as my window manager. No problems.

For what it's worth...

---

### Post by vexorian on 2012-09-26
> **outolintu said:**
> I tried totally re-installing whole Ubuntu 12.04 and downloading all the nessessary updates and additional drivers, still nothing.

Really starting to wonder what is my Ubuntu missing?
Until compiz gets a feature to disable compositing while playing full screen applications. This will always be the case.

But like I mentioned, you can just install a light DE, and use it exclusively when you want to play games. People use lubuntu , xubuntu or gnome-fallback. I go the extra mile and use a single-terminal sesion.

---

### Post by TooManyFeet on 2012-09-27
> **outolintu said:**
> I tried totally re-installing whole Ubuntu 12.04 and downloading all the nessessary updates and additional drivers, still nothing.

Really starting to wonder what is my Ubuntu missing?

If you put: ```
glxgears
``` I presume it comes up with the same error?

---

### Post by outolintu on 2012-09-27
> **TooManyFeet said:**
> If you put: ```
glxgears
``` I presume it comes up with the same error?

This is what comes:

owner@owner-ubuntu:~$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

---

### Post by TooManyFeet on 2012-09-27
> **outolintu said:**
> This is what comes:

owner@owner-ubuntu:~$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

Your graphics drivers aren't working, hence why you're having all these problems.  I stick to nvidia, but it does look like the 5650 has some problems in Ubuntu.  It appears that you should be using ATI's drivers as opposed to the open source ones and [this](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Using_Ubuntu-supplied_fglrx.2FCatalyst) may help (fglrx/catalyst is the driver you want).

To be honest, I would post over in the multimedia / sound section of these forums as it's clearly a video driver issue.  Other than that, there's a few previous posts on these forums (just google Radeon 5650 ubuntu).

Sorry I can't be much more help.

---

### Post by PaulInBHC on 2012-09-27
I have a 5670 1g PCI 16 card and use the settings>additional drivers> the second choice.

Used these since day one and haven't had any problems.

---

### Post by outolintu on 2012-09-28
I'm using Acer TimelineX 3820TG laptop and I'm not sure if the problem has something to do with the fact that this laptop has Intel GFX & ATI Mobility Radeon HD 5650, and it should switch between them on power saving mode.

On Ubuntu this does not seem to work and Intel GFX is active most of the time (at least that's what the system details say). So I don't know if that's the problem. Does anyone know if there is any way to try change it manually from somewhere on Ubuntu?

---

### Post by jadus on 2012-09-28
Guys, i found where the problem is. When i switch to integrated Intel graphics (i have hybrid graphics) everything works fine. Unity 3D works, OpenGL acceleration works, but it's integrated, i want to use dedicated graphics... in unity_support_test everything is YES but OpenGL vendor is Intel Sandy Bridge on MESA... I hope new drivers, now in beta, will solve this problem. When i tried install beta drivers, Xorg won't start, so i must wait for release now :/ Well but i hope it will be good in near future

---

### Post by jadus on 2012-09-30
Okay, i solved this problem. Just install new fglrx drivers, if you have AMD graphics card. And also install 32bit libraries if you have 64bit Ubuntu. Glxgears now showing 700+FPS, before installation it was only <200

---

### Post by naknak987 on 2012-10-01
ok, I just want torchlight to play fullscreen. Im not experiencing anyother problems besides playing it in fullscreen.
If I use a terminal to switch to metacity it plays in full screen, but no menus apear and i cant get it to switch back to compiz without restarting the computer. 
I was wondering if you would help me make a shell script that will switch to metacity, run torchlight, then switch back to compiz after I exit the game. I tried this with no luck.

```
metacity --replace
/usr/local/games/Torchlight/Torchlight.bin.x86
compiz --replace
```

I dont know much about makeing shell scripts so im not surprised it didnt work.

---

### Post by thatguruguy on 2012-10-01
> **naknak987 said:**
> ok, I just want torchlight to play fullscreen. Im not experiencing anyother problems besides playing it in fullscreen.
If I use a terminal to switch to metacity it plays in full screen, but no menus apear and i cant get it to switch back to compiz without restarting the computer. 
I was wondering if you would help me make a shell script that will switch to metacity, run torchlight, then switch back to compiz after I exit the game. I tried this with no luck.

```
metacity --replace
/usr/local/games/Torchlight/Torchlight.bin.x86
compiz --replace
```I dont know much about makeing shell scripts so im not surprised it didnt work.

You may want to read [this]("http://ubuntuforums.org/showpost.php?p=12251114&postcount=12").

---

### Post by naknak987 on 2012-10-01
Actually that worked perfectly. At first I was like, dang I did that yesterday and it didn't work. But then I remebered I had full screen set to 1 not 0. lol.

---

### Post by richi902 on 2012-10-01
i have 
intel i3-2120 and a HD7750 and 8GB ram.  i can play all games fine in fullscreen from the software center in unity with catalyst 12.8 and 12.9-Beta. the only game that dosent really work is torchlight, but the porter from this game said he will fix it, and upload a working build to the software center once it's done, the only bug that is left is the no-faces bug i think, hope he gets it fixed soon.

---

