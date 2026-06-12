---
title: "My experience with WoW and Wine  (commentary &amp; 2 question)"
date: 2006-11-13
forum: Gaming &amp; Leisure
---

### Post by ImaMadGoat on 2006-11-13
I picked up the new version of Ubuntu last weekend and fell in love with it immediately. Especially the beryl desktop eye candy...OMG. There was one thing that I was concerned with, World of Warcraft. I had attempted a switch over the summer with Cedega and Dapper, I finally got fed up with it and went back to Windows until last weekend.

So I gave WoW a shot again with Cedega. I had already installed the 9xxx drivers from nvidia and got beryl to go with it. I soon found a major graphical error with World of Warcraft on Cedega with the 9xxx drivers (the black box bug), but I didn't want to switch back to the 8xxx series. 

So then I decided to give Wine a shot. I must tell you I can not believe how smooth everything went. I can play WoW with beryl ON! Not that I prefer to, but just the fact that I can do it makes me happy. 

I'm getting performance on par with WoW on windows (minus the 4x multisampling). 

So overall, I'm happy. I can't believe that I have no reason to boot over to windows. 

One concern I have however is the high rate that my cpu is running. I don't experience any lag in game or when I switch to my desktop but while WoW is onscreen, the CPU is near 100% constantly. Is this abnormal?

I haven't gotten into the sound issues as far as running teamspeak for raids and such. If anyone has anything they could offer to help with that I'd appreciate it.

Btw, System specs

Ubuntu 6.10 (edgy)
Gnome user
Intel P4 S478 2.8Ghz
1 Gig RAM
Nvidia 6600GT 128MB
Asus P4P800SE Board

Running wow fullscreen in opengl, 1280x1024 resolution. FPS anywhere from 20-50.

---

### Post by FusionXN1 on 2006-11-13
Thats great! Thanks for the info mate. Im thinking of going ubuntu.

---

### Post by chriscando on 2006-11-13
While WoW is running I dont think it would be unusual that the cpu would be at 100%.
Nice to hear installation went smoothly.

---

### Post by casperiv on 2006-11-13
Did you follow one of the howto's on WoW or did it just work with 9.25?  I installed 9.25 and my Diablo II works great.  When I run WoW it runs slow and not at all with opengl.  I tried following [this thread]("http://www.ubuntuforums.org/showthread.php?t=290761&highlight=wow+wine") as well as another, without success.  Whenever I do what howto's tell me my other windows apps don't work anymore.

---

### Post by alinuxfan on 2006-11-13
supposedly with the new wine release it fixed the need to --opengl WoW.
I will not be home until this weekend to try it out.  If anyone has it working let me know
I, too, have had an easy time with Edgy + WoW + Beryl
I keep hearing horror stories of people switching to Edgy.  I am glad I wasn't one.  And to those of you who were, thanks for squashing the bugs :p

---

### Post by ImaMadGoat on 2006-11-13
I copied the Dx folder, the installer.exe file, and the Tome.mpq files from each CD to a folder in my home folder

then I navigated to the folder in a terminal, typed wine installer.exe and got the gui to come up. I installed right from there. Then I moved the 2 patches I needed into the World of Warcraft folder, started up the game and let the patching commence. Once that was finished, I copied my WTF, WDB, and Interface folders from windows to Linux so that I had all my addons and their proper setups all ready to go. 

I did a lot of reading of various guides and posts but I didn't get the entire process from a single one.

---

### Post by hikaricore on 2006-11-13
> **casperiv said:**
> Did you follow one of the howto's on WoW or did it just work with 9.25?  I installed 9.25 and my Diablo II works great.  When I run WoW it runs slow and not at all with opengl.  I tried following [this thread]("http://www.ubuntuforums.org/showthread.php?t=290761&highlight=wow+wine") as well as another, without success.  Whenever I do what howto's tell me my other windows apps don't work anymore.

> **alinuxfan said:**
> supposedly with the new wine release it fixed the need to --opengl WoW.
I will not be home until this weekend to try it out.  If anyone has it working let me know
I, too, have had an easy time with Edgy + WoW + Beryl
I keep hearing horror stories of people switching to Edgy.  I am glad I wasn't one.  And to those of you who were, thanks for squashing the bugs :p

After switching to edgy from dapper I've not been able to run WoW in opengl mode with any build of wine.  I've even tried compiling myself /w and w/o patches to no avail.  I'm guessing the main cause is my video drivers and that I have X set in 16bit colour.  I can live with wow not working due to the fact that everything else I run in opengl mode runs 100x faster.  =)  Anything more than 16bit colour kills my poor little integrated intel chipset hehe.

---

### Post by reiki on 2006-11-14
OK, that was my thread referred to above so I'm going to jump in here and update. :)

I was running Wine 0.9.24 (obviously) and had WoW running fine in OpenGL mode. Just last night I let me system grab the wine 0.9.25 update. I was a bit hesitant only because I had WoW working fine in 0.9.24, but... I let it happen. Wine 0.9.25 works fine right out of the box on Edgy. No problems whatsoever. 

I'm using the 8776 nVidia driver on a 512meg GeForce 7300GT card. WoW is s..m..o..o..t..h !!

I added teh one regedit tweak found [ here](http://appdb.winehq.org/appview.php?iVersionId=5606) that says it's for ATI text rendering issue but works on nVidia. And basically that one tweak just about doubled my framerate.

---

