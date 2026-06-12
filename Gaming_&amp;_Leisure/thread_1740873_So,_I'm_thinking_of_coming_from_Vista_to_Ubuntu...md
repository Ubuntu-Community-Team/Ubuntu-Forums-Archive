---
title: "So, I'm thinking of coming from Vista to Ubuntu.."
date: 2011-04-27
forum: Gaming &amp; Leisure
---

### Post by Phaze08 on 2011-04-27
Ok, so I've always thought it would be cool to try Ubuntu and it seems to have alot of cool features and be really cool and popular. If I was to try it, I would need to be sure of one thing-I could play World of Warcraft. I know, I've read about WINE, but is it stable? Fast? Compatible with different hardware? Support good resolution? I need to know these things before I try the switch...Any feedback would be appreciated. Thanks. :D

---

### Post by Phaze08 on 2011-04-27
One more thing I need: Zune. I think it could probably run in Wine, but I have no idea as I have never used linux. Going to try it out first of course. If anyone knows if this will work that would be awesome, cuz thats what I have lol. Not a big fan of apple so a Zune it was.

---

### Post by Megaptera on 2011-04-27
Something to have a look at until others respond with more specifics ...
[http://wine-review.blogspot.com/2010/01/running-world-of-warcraft-in-ubuntu.html](http://wine-review.blogspot.com/2010/01/running-world-of-warcraft-in-ubuntu.html)

---

### Post by Pierrick584 on 2011-04-27
for lolzune i believe Banshee or Rythmbox will support it out of the box, dint tried it myself but i've read about it, you could try that on a live cd, for WoW, i can guarantee you that it does work, i play on retail, and sometime on private server of every expansion, and it always run out of the box and flawlessly, you only have to run it with the command -opengl, same as windows if you want opengl there, Blizzard do not officialy support linux, the only reason there's no linux client is cause they dont wana hire people to answer phone call of linux users, cause blizz devs do have a WoW client, BUT all that to say that blizzard at leats make sure it does work good with wine, so its extremely rare that you have issue with it under wine, some people have better performance, some others have worse, or similar, but in any case its nothing to worry about unless your computer realy suck

---

### Post by cipherboy_loc on 2011-04-27
Rather than switching entirely, you could add ubuntu as an alternate OS. Then you can see if it works (make sure you try it out thoroughly via the LiveCD first), and if you need any drivers. What hardware are you going to run it on? 


Cipherboy

---

### Post by messelink on 2011-04-28
WoW:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549&iTestingId=62448](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549&iTestingId=62448)

I would recommend to install it using PlayOnLinux (it's a wrapper for wine), it probably has a install script for WoW.

---

### Post by Pierrick584 on 2011-04-28
> **messelink said:**
> WoW:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549&iTestingId=62448](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549&iTestingId=62448)

I would recommend to install it using PlayOnLinux (it's a wrapper for wine), it probably has a install script for WoW.


yes it do, but its 100% useless, if he arleady got WoW installed (duh, obiviously he do) running the install off his windows partition will run very well, just give wow.exe the permission to be executed, and for better performance, make a a file named something like opengl.sh and type in it


wine ./Wow.exe -opengl


then you give execute right to the script, and you run it

---

### Post by Ctrl-Alt-F1 on 2011-05-01
> **Phaze08 said:**
> Ok, so I've always thought it would be cool to try Ubuntu and it seems to have alot of cool features and be really cool and popular.

Honestly, if those are your reasons for switching, I wouldn't do it.  I use Ubuntu because I like the Linux Free/Open Source Philosophy.  When I'm not running a dual boot system with Windows, I usually don't play a lot of graphics heavy games.  This isn't because Linux can't handle 3D games, it's because the Linux Market is an afterthought to Hardware Manufacturers who produce the drivers to make it all work.

Having said that Ubuntu is a great OS.  I use it more than windows, because it operates much faster on my system.  (Which is more than capable of running hot 3d games on Windows).

---

### Post by KingHanco on 2011-05-01
I wouldn't switch because I'm a gamer. Linux isn't a true gamer support.

1. Ubuntu can't run windows games. Only run Linux games.

2. Wine is unstable and so buggy. It will never be stable. What I'm saying is don't think it will run online games in full speed and max graphics. So stay with windows for those cool windows online games. Not every companies will make Linux port of those online games.

For example here: No Linux port on WoW, Rift, Lotr and some others.

---

### Post by Kenjitamura on 2011-05-01
WoW plays with better performance for me in Ubuntu/Wine than it does Windows, you just have to be sure you're using it in openGL mode.  I play Rift in Wine as well but because it doesn't have an OpenGL mode I take a big hit in FPS.  So to summarize any game ported to Mac or generally has OpenGL support will play flawlessly under Wine.  I have a Zune, as always Microsoft is very strict with their security on hardware, last I checked a year ago Zune's could not be used under ubuntu and you had to have Windows to add/delete media to them (this was however a year ago).

The best option would probably be to dual boot Windows and Ubuntu.  I have a quad core processor so what I do is use Virtualbox with one of my cores to run Windows XP for programs I can't get to work under Wine.

---

### Post by Tweak42 on 2011-05-02
> **Phaze08 said:**
> Ok, so I've always thought it would be cool to try Ubuntu and it seems to have alot of cool features and be really cool and popular. If I was to try it, I would need to be sure of one thing-I could play World of Warcraft. I know, I've read about WINE, but is it stable? Fast? Compatible with different hardware? Support good resolution? I need to know these things before I try the switch...Any feedback would be appreciated. Thanks. :D

Yes, you can play Wow using wine because of it's popularity, when it gets completely broken, it gets fixed fairly fast.  Biggest issue is don't try running it on intel or older radeon video hardware because of the performance hit and or buggy drivers.  There are a ton of wow topics if you search the wine forum.

Since wine support for USB devices isn't so good atm, Zune is best run on windows in a VirtualBox instance.

---

