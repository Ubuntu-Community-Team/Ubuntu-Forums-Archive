---
title: "Windows-games on Ubuntu: What are my options?"
date: 2006-05-30
forum: Gaming &amp; Leisure
---

### Post by Sushi on 2006-05-30
OK, I'm totally sick and tired of Windows. I just can't handle the constant hassle, viruses, crummyness and overall suckiness that is Windows. But the thing is that I do occasionally play games, and I play them in Windows. So I need to have a system that I can play games with. There might also be some occasional "productivity"-apps that need Windows, but games are the main area I'm interested in. So what are my options really? I welcome any suggestions and feedback. It seems that I have basically these options:

**Wine**

Free and easily available. But how well does it work with games?

**Cedega**

Costs money, but propably works better than straight Wine. Easier to use. But how fool-proof is the emulation? Would most of my games still not work?

**VMWare**

Costs even more money, but there should be no compatibility-problems since it runs Windows. But what about performance? Also, would VMWare Player (a free download) be enough for my needs?

---

### Post by KingBahamut on 2006-05-30
Wine -- [http://appdb.winehq.org/](http://appdb.winehq.org/)

Cedega -- [http://transgaming.org/gamesdb/](http://transgaming.org/gamesdb/)

VMWare -- Ive heard stories of getting OpenGL/3daccel running on VMWare can be a little touchy at times.

---

### Post by Sushi on 2006-05-30
[QUOTE=KingBahamut]Wine -- [http://appdb.winehq.org/](http://appdb.winehq.org/)

Cedega -- [http://transgaming.org/gamesdb/](http://transgaming.org/gamesdb/)

VMWare -- Ive heard stories of getting OpenGL/3daccel running on VMWare can be a little touchy at times.[/QUOTE]

Well, I do know the websites of the projects, and I have checked them. But I'm looking for additional information that is not found on those websites. True testimonials,  first-hand comments etc.

---

### Post by KingBahamut on 2006-05-30
Well the Wine Apps DB has all working apps on it. Similarly does the Cedega games db. So if your asking how well games work with those applications, what games they are, and on what level they do work, then those sites are ones you need to look at, listed above. 

If your asking for viability , just in general, then I can say its 3 ways up the middle. Yes, Wine will run games, how well will it run them , hard to say. Yes Cedega will run games -- will it run things standard wine will not? It might, it might not. VMware will run games, but at a severe taxing to your system, and will require severe tweaking , or at least thats my impression. 

If none of these help, then list what your playing (or want to play) and we will tell you how viable a solution you need to consider.

---

### Post by eqisow on 2006-05-30
For me, Wine always runs stuff faster than Cedega. However, Cedega seems to be able to get more things to run. VMWare will be much too slow I think, unless you're running a monster of a system.

I think the choice between Wine and Cedega really depends on what you want to run; maybe you should let us know what games you want to install.

Also, there's no reason you can't start with Wine and then get Cedega later if it's needed.  You can even have programs "installed" to both by creating folder links in their virtual drives. This way the program is installed on both, but is only on your HD once.

---

### Post by Sushi on 2006-05-31
OK, thanks for the replies so far :). The list of games is (currently) this:

Civilization III & IV
Combat Mission 1 & 2
Max Payne
Europa Universalis 2
Steam (Half-Life 1 & 2, Counterstrike, Day of Defeat etc.)
Severance
Flashpoint Germany
etc.

Good news is that quite a few of those are not really system-intensive. Bad news is that quite a few of them are not widely played, so they might not be top-priorities for Wine & Cedega.

---

### Post by eqisow on 2006-05-31
The only one of those I have any first hand experience with is Steam. You will need to install a few fonts in Wine to get Steam to run, but once you do that there should be no problems. HL1, CS 1.6, etc all run flawlessly under either Wine or Cedega since they have an OpenGL mode.

Half-Life 2 and it's mods will also run under both Wine and Cedega. However, since Valve was corrupted and only made HL2 available in DirectX you will notice a substantial drop in performance with either. If you don't have GeForce 6800 with 1gig RAM or better I probably wouldn't even try it.

The best thing to do I think, is to grab Wine and start trying things. If Wine can't satisfy you, try Cedega. Also, you may have some luck finding games that are similiar to ones you like, but have better support in Wine/Cedega.

(There is also a Civilization clone for Linux called FreeCiv. It's not very flashy, but the core gameplay is there.)

---

### Post by markr on 2006-05-31
You will have problems running 3d games in vmware.  I believe vmware has experimental drivers for 3d, but all it does is effectively emulate your hardware (hence 'virtual').  I'd think that vmware is pretty much a no go.

I use wine sucessfully with Diablo II, I think it depends on how old the games are. If you are looking at running very new games, I don't think you'll have much success; older games are much more likely to work because people have had chance to do the groundwork and get them running.

I think Cedega has a webpage with all the games that are known to work.

---

### Post by siorai on 2006-05-31
[http://transgaming.org/gamesdb/]("http://transgaming.org/gamesdb/") - The Cedega/Transgaming games database.

---

### Post by mattisking on 2006-06-01
You'll have trouble on alot of games if you are running an ATI card. The Linux drivers are not "complete". It's a shame... even with Cedega (which works well) I can't run many games, even with my ATI X800 All In Wonder.

---

### Post by glotz on 2006-06-01
Kinda offtopic (sosumi) but here goes anyways...

DOS games on Ubuntu: What are my choices?
* [http://dosbox.sourceforge.net/](http://dosbox.sourceforge.net/)
* [http://dosemu.sourceforge.net/](http://dosemu.sourceforge.net/)

---

### Post by B0rsuk on 2006-06-02
Do you think I could run 2D games with Vmware Player (without hardware acceleration) ? The free version available in Dapper ?
I'd love to try out
[http://en.wikipedia.org/wiki/Age_of_Wonders:_Shadow_Magic](http://en.wikipedia.org/wiki/Age_of_Wonders:_Shadow_Magic)
They say no 'modern' game is closer to Master of Magic !

---

### Post by Old on 2006-06-02
To say thank you to you gentlemen seems so inadequate.  Your professionalism in your answers and also the attitude used in your answers is beyond reproach.

It has many years and years since I have thought about Linux but because of my grandchildren and my great-grandchildren, I would like to see them enter computers with Linux.

So now, at my age I must try to learn new tricks. As you know, children are very interested in game's. Hense, the reason for my being in this particular section.
thank you

---

