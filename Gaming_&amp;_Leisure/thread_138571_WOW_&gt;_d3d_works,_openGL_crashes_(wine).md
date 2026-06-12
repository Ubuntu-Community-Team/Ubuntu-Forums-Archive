---
title: "WOW &gt; d3d works, openGL crashes (wine)"
date: 2006-03-02
forum: Gaming &amp; Leisure
---

### Post by lox on 2006-03-02
ok, this is plain WEIRD :D
i've followed many guides.. and after following the on on this forum i got wow updating(6x) > logging in > choosing character > entering world > seeing people walk, interface is here and, ZAP.. i'm stuck (indoor outdoor, anywhere!)
i change my config to d3d, and wow runs! (it gives a directX error, but the games stays up with 30fps in quite places, i can click anything, go in and outside buildings and there aren't any strange textures)
the problem i'm experiencing is that on crowded spots, with people casting etc.. d3d jast becommes laggy, and i have the Xiwndows pointer over the wow pointer (even in fullscreen mode)

so i know wow works.. it runs nicely, but to optimize my performance i wan't OpenGL.. i have working openGL games.. without any troubles, so my drivers must be good, but i can't find any documentation on d3d working while OpenGL doesn't!?

do i need to reinstall my drivers? or, well i really don't know where to go from here! :mad:

---

### Post by meborc on 2006-03-02
what 3d card do you have? if u are one of the un-lucky ATI owners, then you have a long road to getting the best out of your card... and that is probably why you find WoW lagging...

---

### Post by lox on 2006-03-02
well, the 4 seconds i see wow running in openGL are smooooootheee!!!
and d3d is pretty ok, just not like windows..
yes Ati Radeon X800 GTO :(
i'm just looking for the answer to why does it crash after 4 seconds? and why d3d reporting way more bugs, but not crashing or slowing down, or anything :D

---

### Post by meborc on 2006-03-02
well... the forum here is full of *HELP* cries from ATI users... don't dispair... you rae not alone :D ... unfortunately, there is no ONE right solution for the locking up problem (you might try to search for that) ... although there are some more lucky than the others, who might *show us the way*...

i'm watching this with small distress, cuz i'm planning on buying a notebook with ATI X600 128MB card in it... but since nVidia is so much better choice at the moment, i might reconsider...

---

### Post by dantum on 2006-09-20
I have a similar error with my WoW. I works perfectly on my nvidia based desktop. But on ATI HP laptop it dies right after i enter the world. Outside or inside, it freezes up the system. I have to set a timed kill -9 WoW.exe in order to avoid hard reset.

It does it both with Cedega and Wine. It also does it in both D3D and OpenGL modes.

Have you had any success in avoiding the error?


Edit: I just followed some example on this page: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) 

I moved the Survey.MPQ file and chmod 555 the WDB directory. I now can run the game in d3d mode with very much corrupt visuals. I also noticed a wierd thing. I was able to load up OpenGL mode with my character while he was dead. And then ressurect him. When he came back to life the game run for a bit longer but then crashed as usual.

Btw i use "at" command to schedule WoW.exe kill command as my laptop keyboard freezes up when the game crashes and needs a hard reset if process is not killed.

---

### Post by MemoryDump on 2006-09-20
I followed all the instructions I could find about getting WoW to work under Wine and I simply can't get it work.

when I run: wine wow.exe -opengl

WoW tries to load and then I'm presented with an error msg:
"World of Warcraft was unable to start up 3D acceleration"

I have a Nvidia 7800 OT video card and I believe I have the proper drivers working properly. (I used "envy" and I get the Nvidia white boot screen flah when Xorg loads up)

Am I missing something? I'm also not getting any sound.. this is a new install of Unbuntu and I have an Audigy2 sound card. I still have the built-on sound card on my Asus board enabled. (I use that sound card for my headset) Not sure how to make the entire system to use the Audigy2 card as it's default sound card.. and to use oss

Thanks
-MD

EDIT: WoW does load if I type: "wine wow.exe -d3d" but it's EXTREMLY slow and it's not running in full screen mode. (btw this is my first time trying WoW under Linux)

---

### Post by dantum on 2006-09-20
I just installed a Demo of Unreal Tournament 2004 Demo to test teh perfomance of OpenGL and to see if it actually works at all.

With old ATI drivers i had a problem where there was a jerk every 3 secs and it made the game unplayable. Same was affecting Google Earth that runs on OpenGL.  Now OpenGL application doesn't do that but perfomance of UT2004 is still very poor. 

I used the latest wine source from WineHQ and compiled wine with ati patch. I don't think wine is to blame for game crash. I think it's something to do with part of the rendering system that is not properly supported by thje driver. Switching things off and then back on 1 by 1 is one method to test what it is.

Lox try running Google Earth to see if your OpenGL works at all.

---

### Post by Ferrat on 2006-09-21
It's a know bug, you need to recompile wine with the patch for ATI 

HowTo here 
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

Problem is in cities and houses the minimap crashes (goes white) and all the text gets scrambled, with d3d you get mega grafic errors on buildings and freeze 0,5 sec every time you select a new target =(

But except for the text bug in cities the patch works perfect

---

### Post by MemoryDump on 2006-09-23
so nobody has a fix for this using a Nvidia card?
I know the card drivers are working fine as I can run Google Earth no problem.

help?
-MD

---

### Post by Ferrat on 2006-09-24
> **Ferrat said:**
> It's a know bug, you need to recompile wine with the patch for ATI 

HowTo here 
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

Problem is in cities and houses the minimap crashes (goes white) and all the text gets scrambled, with d3d you get mega grafic errors on buildings and freeze 0,5 sec every time you select a new target =(

But except for the text bug in cities the patch works perfect

Fix for not getting your text scrambled when entering cities, just close the minimap before you enter =D

---

