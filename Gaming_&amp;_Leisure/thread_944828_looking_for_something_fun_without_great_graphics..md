---
title: "looking for something fun without great graphics."
date: 2008-10-11
forum: Gaming &amp; Leisure
---

### Post by nibon on 2008-10-11
**Greetings stranger!**
I have an ATI Radeon 9800 card and most games just dont work because of too good graphics. Older games such as Tremolus and nquake runs perfectly but games with better graphics like Savage doesn't. I want to find some more fun games, without DX5000 graphics or WINE that will work, prefferably with online multiplayer, please help<3

---

### Post by Jim! on 2008-10-11
You could give Unreal Tournament and Half Life a shot.

---

### Post by swimb on 2008-10-11
Try Nexuiz, works nicely on my nv6800

---

### Post by MaxIBoy on 2008-10-11
Unreal Tournament: Game Of The Year will work without a problem, if you're willing to buy it (these days it's only available on Steam or bundled with other games of the Unreal series.) 

OpenArena (free game) will also work without a problem, if you're willing to deal with bad maps and bad weapon balance.

---

### Post by eragon100 on 2008-10-12
Urban Terror, it's a *very* fun game and it will run perfectly.

get the latest version from [www.getdeb.net](www.getdeb.net)

it's a violent (Yippie!), realistic, first person shooter based on the quake  engine (same engine as tremulous.)

---

### Post by nibon on 2008-10-12
I have like 10 fps when playing openarena, so I guess that Urban terror won't work either. haven't looked into UT or Nexuiz yet, thanks.

---

### Post by spoons on 2008-10-12
10FPS? I'm sure I got more than that on a GeFoce FX5600 1280 x 1024 with everything at max?!?

---

### Post by nibon on 2008-10-12
I asked a friend and he said that it probably was because I used an ATI card, the ATI drivers are intercoursed up.

---

### Post by simtaalo on 2008-10-12
anyone got any ideas for non FPS games. i do have a good graphics card so thats not a problem. just wondering about any other type of games, something a little different maybe, but preferably something native to linux dont want something runnning on wine.

---

### Post by GSZX1337 on 2008-10-12
> **simtaalo said:**
> anyone got any ideas for non FPS games. i do have a good graphics card so thats not a problem. just wondering about any other type of games, something a little different maybe, but preferably something native to linux dont want something runnning on wine.

Cave Story, or Super Tux, Secret Maryo Chronicles?

---

### Post by Perfect Storm on 2008-10-12
> **simtaalo said:**
> anyone got any ideas for non FPS games. i do have a good graphics card so thats not a problem. just wondering about any other type of games, something a little different maybe, but preferably something native to linux dont want something runnning on wine.

Open Transport Tycoon 
Simutrans 

[quote=nibon]æooking for something fun without great graphics.
Greetings stranger!
I have an ATI Radeon 9800 card and most games just dont work because of too good graphics. Older games such as Tremolus and nquake runs perfectly but games with better graphics like Savage doesn't. I want to find some more fun games, without DX5000 graphics or WINE that will work, prefferably with online multiplayer, please help<3[/quote]

[ttyQuake](http://gaming.gwos.org/doku.php/games:alphabetical:t:ttyquake)

---

### Post by mikedep333 on 2008-10-12
Actually, a radeon 9800 is pretty good. Savage (1) ran beautifully on my radeon 9700 in my athlon xp 1900+ system. There must be a software issue with your system. You can certainly try switching between the open source and the proprietary ati drivers.

---

### Post by nibon on 2008-10-12
ive tried using different drivers, installed them differently, it just wont work under Linux, although on XP I can run Savage, Quake 4 and even FEAR.

---

### Post by MaxIBoy on 2008-10-12
If you can play FEAR on Windows but not even OA on Linux, chances are you don't have 3d acceleration enabled and you're using software rendering. The open source drivers work well for 2d acceleration, but for 3d acceleration they're not so good. For gaming, you'll want the restricted (closed source) drivers.

Try this for installing the drivers (Method 1 doesn't work so well. Use method 2.) [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8_or_8.9.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8_or_8.9.29) Follow the instructions carefully, and you should be okay.

If that doesn't work, ask for help in IRC.

---

### Post by eragon100 on 2008-10-13
> **MaxIBoy said:**
> If you can play FEAR on Windows but not even OA on Linux, chances are you don't have 3d acceleration enabled and you're using software rendering. The open source drivers work well for 2d acceleration, but for 3d acceleration they're not so good. For gaming, you'll want the restricted (closed source) drivers.

Try this for installing the drivers (Method 1 doesn't work so well. Use method 2.) [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8_or_8.9.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8_or_8.9.29) Follow the instructions carefully, and you should be okay.

If that doesn't work, ask for help in IRC.

Use envy, it's a lot easier.

sudo apt-get install envyng-gtk
envyng-gtk

enter password, then click on "install ATI driver"

Wait till it's finished, reboot pc and you're done :wink:

---

### Post by MaxIBoy on 2008-10-13
I'll have to try that the next time there's a major update.

---

### Post by meborc on 2008-10-13
i have only one suggestion - beautiful game and multiplayer - [http://www.teeworlds.com/](http://www.teeworlds.com/)

---

### Post by nibon on 2008-10-14
> **eragon100 said:**
> Use envy, it's a lot easier.

sudo apt-get install envyng-gtk
envyng-gtk

enter password, then click on "install ATI driver"

Wait till it's finished, reboot pc and you're done :wink:

E: Couldn't find package envyng-gtk

---

### Post by MaxIBoy on 2008-10-14
Try going into the Synaptic Package Manager, going to the "settings" menu, selecting "repositories," and enabling all the different check-marks. Then click "close" and exit Synaptic.

After that, it should work.

---

### Post by nibon on 2008-10-14
> **MaxIBoy said:**
> Try going into the Synaptic Package Manager, going to the "settings" menu, selecting "repositories," and enabling all the different check-marks. Then click "close" and exit Synaptic.

After that, it should work.

still Can't find it.

---

### Post by Perfect Storm on 2008-10-14
```
cat /etc/apt/sources.list
```

---

### Post by meborc on 2008-10-14
how to install envyng - [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by charlieg on 2008-10-18
Not quite what you ordered but I liked these two:
[Fish Fillets]("http://fillets.sourceforge.net/") - A wonderfully hard puzzle-with-story game
[F1Spirit]("http://www.braingames.getput.com/f1spirit/default.asp") - 2D top-down frantic racing

---

### Post by Keen101 on 2008-10-29
try interactive fiction or text adventures.  heh. I used to play those on D.O.S.

hehe. I still like them though.

---

