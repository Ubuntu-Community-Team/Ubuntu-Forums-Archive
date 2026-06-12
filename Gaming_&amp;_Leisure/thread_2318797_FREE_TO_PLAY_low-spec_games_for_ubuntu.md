---
title: "FREE TO PLAY low-spec games for ubuntu?"
date: 2016-03-29
forum: Gaming &amp; Leisure
---

### Post by Hopeatykki on 2016-03-29
Hello! I have been looking for some low-spec f2p games and I have tried openarena, 0.A.D., AssaultCube, Sauerbraten, SuperTux2, Runescape, Minecraft, SuperTux kart, Battle for Wesnoth (sorry if translated wrong, for some reason it says the title in finnish Taistelu Wesnothista) and Warzone 2100. I really didn't like them at all as either my FPS was low like in Minecraft and Runescape (yes, I'm serious) or then they weren't my style. Especially in 0AD I had like 4 buildings and 5 women, 3 soldiers and I commanded my soldiers to go scout. Then a freaking army of soldiers came and r**ed my village and the AI had made practically a little country in there. Well, also I played UrbanTerror, I liked it very much, it looks like CSS. :D I'm looking for some more RPG style game, no I don't fancy for the graphics, but something with quests and stuff. Not 2D if possible. And definitely not turn-based. I'll post you the specs : 



[LIST]
[*]AMD Athlon 2 Dual-Core M340.
[*]AMD Mobility Radeon HD 4530 /4570/545v (no idea what that means)
[*]4 GB RAM
[*]223.2 GB HDD
[/LIST]

---

### Post by mastablasta on 2016-03-30
all of the mentioned games should have played reasonably well on your setup. they do on mine. if they don't then you need to lower some graphic settings.

0 a.d. you probably need to use women to build more buildings, gather food and such to build an army, then go scout.

I don't think I can remember any free to play RPG game. you can look at playdeb if you find anything. 

there are some older windows games that would work well in wine/playonlinux and are available at GOG for very low price. such as for example Morrowind, ArxFatalis... some even have their remake in opensoruce (but they might still require original files). GOG also has some games prepared for Linux.

there are also some good indie games that work well in wine or have native Linux client. they are usually cheap.

also check reloaded.org if you find any interesting remake that works in Linux or that would work well in wine. I know there are some less known games out there that do work in Linux.

---

### Post by MikeCyber on 2016-03-30
Remember playing Burger Time, Donkey Kong, Pacman, Arkanoid etc. on the 80' arcade machines? Then you will love Mame.

---

### Post by linuuxi on 2016-04-02
If you liked Urban Terror then maybe you should try Team Fortress 2 as well. It's a multiplayer FPS game (free of course!).

There are lots of free rpg games like FreedroidRPG (sci-fi style), UnReal World, Heroine's Quest: The Herald of Ragnarok, ...

I think you'd enjoy some of them.

---

### Post by mastablasta on 2016-04-04
just looking for some games on my own. and remembered these gems that were released by their makers: 

these should work well in wine/playonlinux or dosbox: 
Command & Conquer
C&C: Red Alert
TES: Arena
TES II : Daggerfall

2 more free FPS:
Enemy territory (add Omnibot if you want to play by yourself or with some friends against or with bots)
WOP (World of Padman), multiplayer game but comes with bots built in.
Smokin Guns - another Q3 based multiplayer with bots.

Space flight sim free
Vegastrike
And Vegastrike based Privateer remake: [http://privateer.sourceforge.net/](http://privateer.sourceforge.net/)

flight gear flight simulator - but you need to reduce quality probably.

---

### Post by sgian on 2016-04-12
I play minecraft on an AMD Athlon 2 dual core 1.6 GHz computer with 4 GB RAM and a slightly newer Radeon card than you have, and there are two things to tweak to make it work well.  The first is to use the proprietary driver, called fglrx.  That makes a big difference in gaming on 14.04, but beware that AMD is dropping support for fglrx in 16.04 as there will be another driver coming out eventually.  Also keep in mind that occasionally the kernel updates might cause a crash with fglrx, but for me the performance increase is worth the slight increase in instability.  The second tweak is to use Oracle Java instead of OpenJDK, but with Oracle Java the downside is that you will have to manually update Java each time there is an update unless you use a PPA and trust that the PPA updates regularly (which it hasn't in the past).  Both tweaks make a huge difference in gameplay with minecraft on 14.04.  If you get the graphics working better with fglrx, then the other games will work better too.

1.  For the driver...Go to "System Settings".  Select "Software and Updates" at the bottom.  Go to the last tab, which is labeled "Additional Drivers".  Let it load, it may take a moment or two.  Select the proprietary driver called fglrx.  I would recommend just using fglrx, and not fglrx-updates, because once you get it working well you don't want to mess with it.  Then after fglrx has installed, reboot.

2.  Java...Easy method is to install the PPA [http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)  However in the past when I used this method, they did not always update regularly and Java needs to be kept updated for security reasons.  The other method is to use the instructions at the following link, but you will have to manually update Java whenever there is an update... [URL="http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html"]https://sites.google.com/site/easylinuxtipsproject/java
[/URL]

---

### Post by mastablasta on 2016-04-13
> **sgian said:**
> I play minecraft 

Minecraft is not free to play.

[QUOTE]
on an AMD Athlon 2 dual core 1.6 GHz computer with 4 GB RAM and a slightly newer Radeon card than you have, and there are two things to tweak to make it work well.  The first is to use the proprietary driver, called fglrx.  That makes a big difference in gaming on 14.04, but beware that AMD is dropping support for fglrx in 16.04 as there will be another driver coming out eventually.

not for this card. this card will have opensource driver only.

---

### Post by deadflowr on 2016-04-13
Freedink.
It's sort of a clone-sque of a zelda like game.
I played it before on an old Pentium4 with an intel 910-something graphics card.
So runs on fairly low specs.
I enjoyed it.
But that's probably just me.

---

### Post by oldrocker99 on 2016-04-13
There aren't very many FOSS RPG games, but GOG.com does sell Neverwinter Nights for $9.95 USD. This thread ([http://ubuntuforums.org/showthread.php?t=2082534&highlight=neverwinter](http://ubuntuforums.org/showthread.php?t=2082534&highlight=neverwinter)) shows how to install the Linux Neverwinter Nights client, which allows complete gameplay. There are **hundreds** of adventures downloadable for free at [http://neverwintervault.org/forums/neverwinter-nights-1/nwn1-modules](http://neverwintervault.org/forums/neverwinter-nights-1/nwn1-modules). You have to buy the game, but there are many many hours of gameplay once you have it, all for free.

---

