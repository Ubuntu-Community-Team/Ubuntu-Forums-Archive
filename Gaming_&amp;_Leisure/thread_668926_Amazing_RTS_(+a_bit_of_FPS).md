---
title: "Amazing RTS (+a bit of FPS)"
date: 2008-01-15
forum: Gaming &amp; Leisure
---

### Post by Vadi on 2008-01-15
Before we begin, take a few minutes to download and watch this video showcasing the game:

[http://www.unknown-files.net/spring/3568/Spring_Trailer_2/](http://www.unknown-files.net/spring/3568/Spring_Trailer_2/)

Hooked? Good, let's continue. Spring really is an Engine that runs the *numerious* mods and maps that are available for it. And it's just the engine only, there are multiple front-ends for it. So, here I'll copy/paste the relevant parts out of their setup wiki, and add some things of my own, to get you started with Spring RTS.

1) Get the spring engine itself. They've setup a Ubuntu 7.10 repository:

> Do the following:

Those lines are long and split to fit on this page, you can copy-paste this to your terminal as is, as long as you copy all lines and not just one.

wget -q [http://buildbot.no-ip.org/~yokozar/apt/387EE263.gpg](http://buildbot.no-ip.org/~yokozar/apt/387EE263.gpg) -O- | \
    sudo apt-key add -

sudo wget [http://buildbot.no-ip.org/~yokozar/apt/sources.list.d/gutsy.list](http://buildbot.no-ip.org/~yokozar/apt/sources.list.d/gutsy.list) \
    -O /etc/apt/sources.list.d/springproject.list

sudo apt-get update
sudo apt-get install spring spring-lobby-springlobby spring-maps-default -y

Also, if you want to download a few large maps you can do following:

sudo apt-get install spring-maps-hunterw spring-maps-deltasiege spring-maps-smallsupreme spring-maps-teamplay

If you own the original Total Annihilation and want to use mods that require the original TA content, you can do:

sudo apt-get install spring-data-nonfree

For configuring the lobbies, you can note that the package installs the Spring executable at /usr/games/spring and read-only data in /usr/share/games/spring. 

That should get you a basic install going. Launch springlobby, and either try playing online, or by yourself. Keep in mind that each mod is different, ie, there may be different units, or the same units but with different qualities.

If you want more maps, the place to find them is here ([click]("http://unknown-files.net/spring/category/13/Maps/")). Just save the files to ~/.spring/maps. For mods, ([click]("http://unknown-files.net/spring/category/13/Mods/")) and save them to ~/.spring/mods

Have fun, and post if you need any help!

---

### Post by Ozor Mox on 2008-01-16
I have watched the trailer quite a few times and the game does indeed look fantastic. There's one thing missing from your post though, and also their setup page. That is, what mod(s) do you install if you *don't* own the original game. There is no indication on the Spring website as to which mods use content from the original game and which use free content. I have been guessing, and deleting the ones that give me "bad cursor error" or something similar, as this indicates they use non-free content. I also couldn't really tell how complete the mods are.

I would love to get this game up and running, any suggestions?

---

### Post by Vadi on 2008-01-16
I don't believe you need the original content for the majority of the mods. At least, the game works fine for me.

And the original game looks to be 2d only, while they're using a 3d engine, so it can't be the original thing..

---

### Post by [L2G] Slapshot on 2008-01-16
Vladi it really does look great. Thanks for sharing that with us mate. I will have a closer look at this in the very near future.


OZOR MOX

Here is a snippet from their main page

Located here [http://spring.clan-sy.com/]("http://spring.clan-sy.com/")



- If you get error: missing default cursor after you downloaded a mod from Unknown Files, download this archive, unzip it, and put the 3 files inside in C:\Program Files\base\ (or wherever you installed Spring). Remember that you may only legally do this if you own the original total annihilation game. If you don't own it, you have to play only mods that don't give this error.

The link on the page goes to here

[http://www.unknown-files.net/spring/3928/OTA_Content/]("http://www.unknown-files.net/spring/3928/OTA_Content/")

I must point out that it says you must own the original Game cd to legally download these files.

Hope this helps

Slap

---

### Post by TheIdiotThatIsMe on 2008-01-16
Looked at it, looks really nice. Was happy, until it went all 3D specials and I realized I cant run it on my Intel card :(

---

### Post by Ozor Mox on 2008-01-16
> I don't believe you need the original content for the majority of the mods. At least, the game works fine for me.

And the original game looks to be 2d only, while they're using a 3d engine, so it can't be the original thing..

Can you tell me what mods you have tried that work and are playable?

> OZOR MOX

Here is a snippet from their main page

Located here [http://spring.clan-sy.com/](http://spring.clan-sy.com/)



- If you get error: missing default cursor after you downloaded a mod from Unknown Files, download this archive, unzip it, and put the 3 files inside in C:\Program Files\base\ (or wherever you installed Spring). Remember that you may only legally do this if you own the original total annihilation game. If you don't own it, you have to play only mods that don't give this error.

The link on the page goes to here

[http://www.unknown-files.net/spring/3928/OTA_Content/](http://www.unknown-files.net/spring/3928/OTA_Content/)

I must point out that it says you must own the original Game cd to legally download these files.

Hope this helps

Slap

Thanks for that info. The trouble is, I don't own the original game, and that has put me off this solution somewhat. I suppose I could always buy it.

EDIT: I have been looking around and found that on the latest news item on the homepage it says that all mods except Balanced Annihilation and XTA are free content, which happened to be the two I tried that didn't work. I'm going to try this out right away!

EDIT the 2nd: Ok that's not true at all as I just downloaded NOTA mod and still get the missing cursor error, which I cannot legally fix. So, back to my original question? What mods are you using that don't require the original game that are good?

---

### Post by Vadi on 2008-01-16
Here at the contents of my folders, if they help any.. I don't have any cursor problems though.

> /home/vadi/.spring/maps/paths
/home/vadi/.spring/maps/BA60.sd7
/home/vadi/.spring/maps/ExpandedTropics.sd7
/home/vadi/.spring/maps/Road_To_Rome.sd7
/home/vadi/.spring/maps/Small_Supreme_Battlefield.sd7
/home/vadi/.spring/maps/SpeedMetal.sd7
/home/vadi/.spring/maps/Tropical.sd7

/home/vadi/.spring/mods/AASpring223
/home/vadi/.spring/mods/AASBase22.sdz
/home/vadi/.spring/mods/AASH22.sdz
/home/vadi/.spring/mods/AASH223.sdz
/home/vadi/.spring/mods/AASHD.sdz
/home/vadi/.spring/mods/AASP22.sdz
/home/vadi/.spring/mods/AASP223.sdz
/home/vadi/.spring/mods/AASS22.sdz
/home/vadi/.spring/mods/AASS223.sdz
/home/vadi/.spring/mods/BA591.sd7
/home/vadi/.spring/mods/Castles.sdz
/home/vadi/.spring/mods/EpicLegionsPublicBetav14.sdz
/home/vadi/.spring/mods/S44LiteRelease.sdz

---

### Post by travist120 on 2008-01-16
I've seen this, looks quiet amazing, but for some reason, even after following the instructions for the default maps and mods, I'm still unable to play any of them. They don't even show up in the spring lobby. I even installed 1 map and 1 mod from downloading it and it still won't show up. I even put it in the right folders and stuff. Right now, I'm downloading the large maps to see if it will take those in, but I don't know why the game isn't working for me.

---

### Post by Draken_1337 on 2008-03-05
Hi! 
If you haven't solved this problem yet:
Just add deb [http://ppa.launchpad.net/spring/ubuntu](http://ppa.launchpad.net/spring/ubuntu) gutsy main
in the repositories and then search for Spring in synaptic and install.
You need to install mods and maps to play, since it's only an engine.
But [http://www.unknown-files.net/spring/category/14/Mods/](http://www.unknown-files.net/spring/category/14/Mods/)
is down for the moment..Check here instead:
- from JJ: [http://spring.jobjol.nl](http://spring.jobjol.nl)
- from Sefidel: [http://www.springplayersclub.com/](http://www.springplayersclub.com/)
- from AF: [http://www.darkstars.co.uk/downloads/](http://www.darkstars.co.uk/downloads/)
- from M_A_D: [http://www.tasdownloads.com/](http://www.tasdownloads.com/)
- from BLC: [http://spring-portal.com](http://spring-portal.com)
- from FA: [http://evolutionrts.info/maps/](http://evolutionrts.info/maps/)
Use automatic p2p map and mod downloader: [http://spring.clan-sy.com/phpbb/viewtopic.php?f=1&t=13990](http://spring.clan-sy.com/phpbb/viewtopic.php?f=1&t=13990)
Search for torrent in downloader repository: [http://tracker.caspring.org/search.php](http://tracker.caspring.org/search.php)

/David

---

### Post by Vadi on 2008-03-05
Maps are in the repository too. Just waiting on the mods...

---

### Post by ELD on 2008-03-05
Your a bit late buddy i have been campaigning this game since it's early development!

[http://ubuntuforums.org/showthread.php?t=203448](http://ubuntuforums.org/showthread.php?t=203448)

---

### Post by Vadi on 2008-03-05
I found Spring Lobby to be better-made :|

---

