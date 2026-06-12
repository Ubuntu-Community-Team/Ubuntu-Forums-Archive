---
title: "The Wine 0.9.31 Thread"
date: 2007-02-18
forum: Gaming &amp; Leisure
---

### Post by YokoZar on 2007-02-18
Hi, I make the Wine packages for Ubuntu.

You can get them from the page I put up here: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

Note that I'm just a packager at this point: I don't write any actual Wine code.   Bug reports should be filed at [Wine's bugzilla](http://bugs.winehq.org/) after looking them up in the [Application Database](http://appdb.winehq.org/).  I do however, maintain the APT repository and the website above, so you can post issues with that here and I'll read them.


Anyway, the purpose of this thread is to talk about the latest version of Wine (0.9.31), as well as how it's working in Ubuntu.  I'll read everything here.

I've already heard about a big regression in CS:Source rendering the game unplayable without unless launching a map upon startup.  This is a shame since this version contains a whole bunch of DirectX fixes and speedups too.

What else have people been experiencing?  Feel free to give thoughts on Wine in general.

---

### Post by zgerrz on 2007-02-18
> **YokoZar said:**
> What else have people been experiencing?  Feel free to give thoughts on Wine in general.

Just a general comment I'd like to make.

I love how quickly wine is being developed, but I just hate how as versions progress sometimes specific games actually play worse (like how you mentioned CS: Source).

I do realize that wine is a very complicated application and problems can be difficult to control, I just wanted to point out this issue. I also realize that as a packager you yourself don't really have much control over this issue either.

---

### Post by YokoZar on 2007-02-18
> **zgerrz said:**
> Just a general comment I'd like to make.

I love how quickly wine is being developed, but I just hate how as versions progress sometimes specific games actually play worse (like how you mentioned CS: Source).

I do realize that wine is a very complicated application and problems can be difficult to control, I just wanted to point out this issue. I also realize that as a packager you yourself don't really have much control over this issue either.We call these breakages "regressions", and unfortunately there's not too much we can do to stop them.  There are thousands of Windows Apps out there, and we have to rely on user-submitted bug reports to spot regressions in each one.

The trouble is, people very rarely run development versions of Wine - the releases are frequent enough (every 2 weeks) that it's a lot less of a hassle to run the latest release than it is to compile from the GIT repository.  What this means is that we have very little means of detecting a regression until the release is pushed.


There is an eventual solution to all of this, of course, and it's to have a slow, stable release process where a particular version is tested for regressions and finally signed off on - exactly like how Ubuntu itself is finalized.  The trouble is, Wine isn't yet in a stage of development where it seems worth it to create such a release upstream - instead, the decision is simply whether or not to use an older version of Wine when deploying it during, say, a distribution release.

---

### Post by cb951303 on 2007-02-18
hello
with the 0.9.31 pack form winehq diablo's sound is broken... does anyone have any idea why?

---

### Post by GFree on 2007-02-18
Well I'm not sure if it was due to the new version of Wine, or whether I touched something by accident and got lucky, but whatever the case I no longer need to close the Steam window before a game launches (i.e. the Steam window no longer remains on top of a game).

The sound in Tomb Raider Legend is very choppy. Apparently it was working better in 0.9.29.

---

### Post by bastiegast on 2007-02-18
Oblivion runs smooth in linux, wine owns cedega :popcorn: which still only has oldoblivion support. Only sound and water shader give problems and still the sneak cursor remains on. Bloom even works! (Although sometimes it has strange issue's). 
Since wine 0.9.31 lots of shaders work making the game just as nice as in windows(apart from water) also I no longer need to play in a virtual wine desktop as my resolution gets restored properly when exiting the game. .31 also fixed issue's I had with saving and crashing. As fas as I can tell the game runs without significant performance loss(It's been I while since I played it in windows).
A few screenies:
Funny bloom glitch (phew a very sunny day in cyrodill):
[[IMG]http://img68.imageshack.us/img68/2472/schermafdrukfl3.th.png[/IMG]](http://img68.imageshack.us/my.php?image=schermafdrukfl3.png)
Playing:
[[IMG]http://img181.imageshack.us/img181/2636/schermafdruk1ea0.th.png[/IMG]](http://img181.imageshack.us/my.php?image=schermafdruk1ea0.png)

---

### Post by Mongoose on 2007-02-18
Yeah, and it's pretty stable too.  I played Knights of the Nine content for 3hrs straight on 0.9.31.  I play in desktop'ed wine with the game fullscreen at 1024x748.

---

### Post by Gamingtao on 2007-02-18
Since 0.9.31 I can't get World of Warcraft back into windowed mode. Inside WoW the grahics config says windowed mode, and checking the config.wtf I still see the entry to forcing it into windowed mode. It was working perfect in windowed mode just before the update.

---

### Post by YokoZar on 2007-02-18
> **Gamingtao said:**
> Since 0.9.31 I **can** get World of Warcraft back into windowed mode. Inside WoW the grahics config says windowed mode, and checking the config.wtf I still see the entry to forcing it into windowed mode. It was working perfect in windowed mode just before the update.I'm sorry, I'm a bit confused here...did you mistype something?

---

### Post by Gamingtao on 2007-02-18
Yep mistype, edited now sorry about that.:lolflag:

---

### Post by function1 on 2007-02-18
stupid post -- problem resolved

---

### Post by Sammi on 2007-02-19
I'm sorry to hear that there have been some big regressions, but I was actually feeling like creating a tread to praise the new version. I used to get a black screen in WoW when running in directx mode, but now it's running at full frame rates, with only a few minor graphical glitches. Opengl is still better, but with this new version the game is actually playable in directx mode, which is very impressive :D

I have 2 gig of ram, a big pentium4 and a Nvidia 6800.

---

### Post by Mekanikka on 2007-02-20
I need help! i just recently transferred from windows to ubuntu, i got wine going and managed to start World of Warcraft. when i start it i get the login screen where the big statue guys are(for those familiar) and its just black with the buttons and the little bars to write account info. so i log on and everything is black, again buttons not included. i can change server and scroll my character list, but the only ones shown are ghosts(no idea why) i click enter world and it crashes(big surpise :P) im a total noob in ubuntu and only really switched because i heard Enemy Territory and World of Wacraft could be run on ubuntu and i wanted beryl.


help?

---

### Post by Sammi on 2007-02-20
You're posting in the wrong tread. I guess you want help with running WoW using Wine, so you should really be posting in this tread: [http://www.ubuntuforums.org/showthread.php?t=312482](http://www.ubuntuforums.org/showthread.php?t=312482)

Also you should read the WoW/Wine howto before you post anything anywhere: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Good luck :D

---

### Post by Sarteck on 2007-02-20
Well, in Diablo II and Diablo II:LOD, as has been mentioned, there is the sound problem...  However, there's also a lot of shadow problems.  For instance, the shadows of many in-game objects (people, monsters, torches, etc.) are actually a reflection of the object rather than a black blur--it's funny to look at, but unintended to be sure. XD  Also, the background of a dialog box (when speaking to people or whatever) is no longer darkened.  Text in those same dialog boxes ("TALK" "TRADE" "CANCEL" etc.) is no highlighted when moused over.  And, though HELL difficulty is not playable for one of my characters yet, it is "lit up" as if it were an option in the list where I select difficulties.



Keep up the good work, and good luck when you do actually start writing the code. ^_^

---

### Post by the_darkside_986 on 2007-02-20
Has anyone gotten Morrowind to work with the new Wine version? I have never had it working in Ubuntu 6.06. Upgrading from .9.9 got rid of the "Unknown stencil format" popup but now it just crashes. Of course, I don't have the log as I am not at my home PC.

---

### Post by Mongoose on 2007-02-20
Morrowind has been running fine aside from 3 minor graphics issues and no music for a while.  I know that 0.9.31 fixed 2 of the graphics issues, and caused a regression of another.

Right now morrowind water 'animation' and projected shadows don't render properly, but you can just adjust the slider to disable the shadows ( they show up white otherwise ).

---

### Post by the_darkside_986 on 2007-02-20
I keep getting an unhandled exception fault after a bunch of error messages about D3D. I'm using the evil proprietary Nvidia drivers that work with my Nvidia 7300 GS. I have no idea how to fix this problem. I'm afraid to even try making Oblivion run if I can't even get Morrowind or Deer Avenger 4 to run in wine. These companies utterly fail at porting a little old executable and writing their crap in multi-platform libraries. So I will just fail to ever buy another product from Bethesda again. Oblivion was a disappointment anyways. (Deer avenger 4--just some old CD of it that some people left behind. I don' t care too much about it. But I really need Morrowind to work because I'm afraid of damaging the ability to complete the story on the Xbox version like I almost did once. I forgot to pick up a quest item before it disappeared and I had to re-load and re-do the whole dungeon again)

I did use the Loki installer for Morrowind so maybe that is the problem...

---

### Post by Shay Stephens on 2007-02-20
version.9.28 and .9.29 broke Photoshop 7, but .9.31 is working, and working better than .9.27.  I am quite pleased from a photoshop standpoint :-)

---

### Post by Drezliok on 2007-02-21
I havn't installed photoshop yet. I've been playing with GIMP

---

### Post by Brynster on 2007-02-22
.31 broke Counterstrike Scource. That to me is a show stopper, so i downgraded back to .30, which works flawlessly as ever.

There is a "fix" available to make CS:source work with .31 and it supposedly works bettter, but until its written in English so a layman can understand it I cannot fix it.

---

